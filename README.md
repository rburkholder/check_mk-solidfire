# check_mk-solidfire
check_mk scripts to collect cluster and volume information from a solidfire system

On my server, I have two scripts, and since this is updated 18 months after the fact, I'm not quite sure of 
all the interactions, but this is what I have:

```
OMD[sitename]:~$ cat /usr/lib/check_mk_agent/local/solidfire.sh
/usr/bin/python /usr/lib/check_mk_agent/checkSolidFire.py <slfr_cluster_ip> 443 rouser password mvip
/usr/bin/python /usr/lib/check_mk_agent/checkSolidFire.py <slfr_node1_ip> 442 rouser password node
/usr/bin/python /usr/lib/check_mk_agent/checkSolidFire.py <slfr_node2_ip> 442 rouser password node
...  more nodes ...

```

```
OMD[sitename]:~$ cat /usr/lib/check_mk_agent/plugins/slfr-cluster.sh
/usr/bin/python /usr/lib/check_mk_agent/SolidFireAgentCluster.py <slfr_cluster_ip> 443 rouser password mvip

```

<b>slfr_cluster</b> - check_mk script to process cluster section<br>
<b>check_mk-slfr_cluster.php</b> - pnp4nagios format

<b>slfr_volumes</b> - check_mk script to process volumes section<br>
<b>check_mk-slfr_volumes.php</b> - pnp4nagios format

<b>slfr_nodes</b> - check_mk script to process nodes section<br>
<b>check_mk-slfr_nodes.php</b> - pnp4nagios format

