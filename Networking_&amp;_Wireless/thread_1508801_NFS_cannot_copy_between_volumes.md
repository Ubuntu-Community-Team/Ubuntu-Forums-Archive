---
title: "NFS cannot copy between volumes"
date: 2010-06-13
forum: Networking &amp; Wireless
---

### Post by mattjones124 on 2010-06-13
I have a drive called Media that I currently share over SAMBA.  I was reading about NFS, and decided I wanted to make the change.  However, the way my Media drive was setup was that there were several symbolic links to other drives with more data, which SAMBA would follow and I would be able to see files from several drives under one file share. 

However, when I switched to NFS, the symbolic links no longer worked.  I read about using mount --bind to perform a very similar function, so I switched to this way of doing things.  I can now read and write to several drives using one network share.

However, when I try to copy between two drives using Mac OS X, I get the following error.

[IMG]http://farm5.static.flickr.com/4007/4696753074_24f3b38bdb_o.png[/IMG]

I did a google search for the error, and it means the following:
HFS Errors     1303     diffVolErr     Files on different volumes

I am not sure this is a problem with my NFS setup, or it is a problem with the Apple NFS client.

Here is my /etc/exports:

> # /etc/exports: the access control list for filesystems which may be exported
#		to NFS clients.  See exports(5).
#
# Example for NFSv2 and NFSv3:
# /srv/homes       hostname1(rw,sync,no_subtree_check) hostname2(ro,sync,no_subtree_check)
#
# Example for NFSv4:
# /srv/nfs4        gss/krb5i(rw,sync,fsid=0,crossmnt,no_subtree_check)
# /srv/nfs4/homes  gss/krb5i(rw,sync,no_subtree_check)
#

/media           		 192.168.1.0/24(rw,fsid=0,insecure,no_subtree_check,async)
/media/storage    		 192.168.1.0/24(rw,nohide,insecure,no_subtree_check,async)
/media/storage/media    	 192.168.1.0/24(rw,nohide,insecure,no_subtree_check,async)
/media/storage/media/downloads   192.168.1.0/24(rw,nohide,insecure,no_subtree_check,async)
/media/storage/media/films       192.168.1.0/24(rw,nohide,insecure,no_subtree_check,async)
/media/storage/media/music       192.168.1.0/24(rw,nohide,insecure,no_subtree_check,async)
/media/storage/media/torrent     192.168.1.0/24(rw,nohide,insecure,no_subtree_check,async)
/media/storage/media/tv     	 192.168.1.0/24(rw,nohide,insecure,no_subtree_check,async)
/media/storage/media/films/A-M   192.168.1.0/24(rw,nohide,insecure,no_subtree_check,async)


Any ideas?

---

