# Clusters

## Commands

### Listing clusters

You can list all clusters currently running in your account by running:

``` R
cluster <- getClusterList()
```

### Viewing a Cluster

To view details about your cluster:

``` R
cluster <- getCluster("pool-001")
```

### Resizing a Cluster

At some point, you may also want to resize your cluster manually. You can do this simply with the command *resizeCluster*.

```R
cluster <- makeCluster("cluster.json")

# resize so that we have a min of 10 dedicated nodes and a max of 20 dedicated nodes
# AND a min of 10 low priority nodes and a max of 20 low priority nodes
resizeCluster(
    cluster, 
    dedicatedMin = 10, 
    dedicatedMax = 20, 
    lowPriorityMin = 10, 
    lowPriorityMax = 20, 
    algorithm = 'QUEUE', 
    timeInterval = '5m' )
```

If your cluster is using autoscale but you want to set it to a static size of 10, you can also use this method:

```R
# resize to a static cluster of 10
resizeCluster(cluster, 
    dedicatedMin = 10, 
    dedicatedMax = 10,
    lowPriorityMin = 0,
    lowPriorityMax = 0)
```

### Getting Files from a Cluster Node
You can download files from a specific node.
```R
getClusterFile(
  cluster,
  "tvm-3601533753_1-20180813t211014z",
  "startup/stdout.txt")
```

