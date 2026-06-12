---
title: "need bittorrent client that quits when download complete"
date: 2009-07-09
forum: Networking &amp; Wireless
---

### Post by beanfield on 2009-07-09
To cut anyone off before they get the wrong idea, I'm not trying to leech torrents off public servers without contributing.  

We're looking for methods to distribute files to computational nodes in our cluster.  The files are probably going to range 5-50G.  The way we currently do it is a job is submitted to a slot on one of our nodes, the job either copies the data locally to the node or just reads the data if it's too large.  The data is shared by a nfs cluster with a shared filesystem.  It works well, until a couple hundred blades all hit the same data at once.

What I'm looking to do now is use bittorrent as a drop in replacement for the cp command.  The problem is that none of the command line bittorrent clients I have found will actually quit the application once the download is complete.  I could run a single bittorrent process per job and fork the bittorrent client off as a child process, but I run into issues with cleanup.  If a job is terminated, or fails, I'm left with a bittorrent process (owned by init, ppid 1) hogging resources (cpu, mem, disk, network, etc...) and I have no way to kill it without logging into hundreds of nodes and manually taking care of each one.

I was also looking using something like rtorrent as a running daemon that controls the torrent distribution for all jobs running on a node (instead of one bittorrent client per job).  Each job could copy a .torrent into a watch dir, rtorrent would start downloading, and rtorrent would move the downloaded data into a completed dir when done downloading.  The job would just have to check the completed dir every couple of secs.  The downsides to this are that I've been unable to get rtorrent to download a .torrent more than once.  It seems once the .torrent and files are deleted, rtorrent puts the session for the torrent download in a closed state and never re-initiates properly if I put the same .torrent back in the watch dir.  Additionally, if two jobs land on the blade that both need the same torrent files, the cleanup portion of one could hork the data for the other.

I'm sure there's ways to get around much of the issues mentioned above, but it would definitely be easiest if I could find a bittorrent client that quits after downloading.

---

