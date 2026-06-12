---
title: "Need help setting up NFS"
date: 2010-07-08
forum: Networking &amp; Wireless
---

### Post by pmooney78 on 2010-07-08
I want to export my music stored on one laptop, my primary one (an HP Pavilion dv6000 running Ubuntu 9.10, 2 gigs RAM) so that I can also access it from my other laptop (Dell Latitude D420 running Ubuntu 9.10, 2 gigs RAM). I'm following the tutorial here: [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

I've installed the nfs-kernel-server (and its dependencies) on the server, and nfs-common and portmap on the client. I've created a directory structure /export and /export/music; /export/music is bound to /home/patrick/Music with the following line in /etc/fstab:

```

/home/patrick/Music				/export/music	none		bind				0	0

```

I've verified that it works across restarts (i.e., /export/music contains my music folders that I expect to be there). I've made the tutorial's suggested changes to /etc/default/nfs-kernel-server and /etc/default/nfs-common (both of which are included in their entirety below) and restarted the service with "/etc/init.d/nfs-kernel-server restart" -- then tried mounting the exported share from the client with 

```

mount -t nfs4 -o proto=tcp,port=2049 192.168.1.101:/export /import

```

/import is a real directory on the client. ifconfig reports that the local-network IP address of the server is in fact 192.168.1.101; the local-address IP for the client is 192.168.1.100. I'm connecting using wired Ethernet cables only across a Linksys router. (I'd eventually like to be able to do this wirelessly, of course, but turned off wireless networking for both computers for now to be able to narrow down potential problems.)

I can't figure out what else to check ... and nothing I've turned up in a quick Google search is helpful. 

Any suggestions much appreciated.

Here's my /etc/fstab from the server:

```

# /etc/fstab: static file system information.
#
# <file system>					<mount point>	<type>		<options>			<dump> <pass>
proc						/proc		proc		defaults			0	0
# /dev/sda2
UUID=b621849b-f092-493e-a140-4a7415485df7	/		ext3		relatime,errors=remount-ro	0       1
# /dev/sda1
UUID=868fab91-c462-4b10-83f6-56e42d4b0b6a	none		swap		sw				0       0
/dev/scd0					/media/cdrom0	udf,iso9660	user,noauto,exec,utf8		0       0
#NFS shares
/home/patrick/Music				/export/music	none		bind				0	0

```

Here's my /etc/default/nfs-kernel-server from the server:

```

# Number of servers to start up
RPCNFSDCOUNT=8

# Runtime priority of server (see nice(1))
RPCNFSDPRIORITY=0

# Options for rpc.mountd.
# If you have a port-based firewall, you might want to set up
# a fixed port here using the --port option. For more information, 
# see rpc.mountd(8) or http://wiki.debian.org/?SecuringNFS
RPCMOUNTDOPTS=--manage-gids

# Do you want to start the svcgssd daemon? It is only required for Kerberos
# exports. Valid alternatives are "yes" and "no"; the default is "no".
NEED_SVCGSSD=no

# Options for rpc.svcgssd.
RPCSVCGSSDOPTS=

```

Here's my /etc/default/nfs-common from the server:

```

# If you do not set values for the NEED_ options, they will be attempted
# autodetected; this should be sufficient for most people. Valid alternatives
# for the NEED_ options are "yes" and "no".

# Do you want to start the statd daemon? It is not needed for NFSv4.
NEED_STATD=

# Options for rpc.statd.
#   Should rpc.statd listen on a specific port? This is especially useful
#   when you have a port-based firewall. To use a fixed port, set this
#   this variable to a statd argument like: "--port 4000 --outgoing-port 4001".
#   For more information, see rpc.statd(8) or http://wiki.debian.org/?SecuringNFS
STATDOPTS=

# Do you want to start the idmapd daemon? It is only needed for NFSv4.
NEED_IDMAPD=yes

# Do you want to start the gssd daemon? It is required for Kerberos mounts.
NEED_GSSD=no

```

And here's the /etc/exports from the host:

```

# /etc/exports: the access control list for filesystems which may be exported
#		to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
# /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)
#

/export       192.168.1.100/24	(rw,fsid=0,insecure,no_subtree_check,async)
/export/music 192.168.1.100/24	(rw,nohide,insecure,no_subtree_check,async)

```

---

### Post by pmooney78 on 2010-07-09
anyone?

---

### Post by JohnYYC on 2010-07-10
When I setup nfs I never edited the nfs-common or nfs-kernel-server config files. I followed this guide [http://clararaubertas.net/blog/share-folders-between-two-ubuntu-computers-on-the-same-lan-with-nfs/](http://clararaubertas.net/blog/share-folders-between-two-ubuntu-computers-on-the-same-lan-with-nfs/) I hope that helps you out.

---

### Post by BallisticBanana on 2010-07-10
I've been having 'fun' with NFS and samba recently.

I've shared my 8.04 'server' folders to my 10.04 'client' desktop using the following syntax in my /etc/fstab ...

```

192.168.1.201:/media/disk /media/Server_Media nfs rw,async,dev,auto,_netdev 0 0
192.168.1.201:/media/disk-1 /media/Server_Data nfs rw,async,dev,auto,_netdev 0 0
192.168.1.201:/media/disk-2 /media/Server_Shared nfs rw,async,dev,auto,_netdev 0 0

```

My server always takes the same IP address - this is reserved by the router (DG834GT) using the server's MAC address.  You could use 'defaults' instead of the rw,sync etc., although I added in the _netdev to ensure the network was detected before trying to mount.

Based on your data provided, maybe your fstab should read ...

```

192.168.1.101:/home/patrick/music /export/music nfs defaults 0 0

```

Your extensive notes makes me feel that my suggestion might be too 'simple' - I'm only a beginner  :)

Now, I'm off to find a solution to my 'not being able to mount a samba (WinXP) share at boot' - same problem as you really.

Good luck!

---

### Post by mal on 2010-07-10
pmooney78,

I have used nfs on my home network for a few years and found it really easy to set up.  The main points are:

- You will need to make sure your server always has the same IP address by using a static IP or configuring your router to always allocate the same address for your server.

- The only configuration needed on the server is to include the required shares in /etc/exports.  Restart nfs-kernel-server after making any changes.

- You should be able to see the available shares by running "showmount -e server" on the client.

- To mount the shares on a client use "mount server:/share/path/ /mnt/share" or include an appropriate line in /etc/fstab.  Make sure to create the mount point on the client first.

Note that there is a bug in mount.nfs that will hang your client machine if it tries to mount a share on the server when the server is not operating or is inaccessible. (see [https://bugs.launchpad.net/dolphin/+bug/164120]("https://bugs.launchpad.net/dolphin/+bug/164120"))

Good luck.

Mal

---

### Post by pmooney78 on 2010-07-11
Bingo. Every single one of these suggestions was helpful in one way or another. I now have my primary music folder exported to my alternate laptop with reasonable options. Thank you all so much!

I just walked backwards through the guide I initially linked, undoing everything, and then followed the guide posted by JohnYYC, then modified the options and my fstab to make it permanent (and read-only, incorporating some other advice). I also configured my router to make sure that each laptop gets the same IP address each time they boot based on MAC address.

It's the community that makes Ubuntu such a rewarding experience, in the last analysis. Thanks again. :D

---

