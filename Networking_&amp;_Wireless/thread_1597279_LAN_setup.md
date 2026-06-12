---
title: "LAN setup"
date: 2010-10-15
forum: Networking &amp; Wireless
---

### Post by bill-lancaster on 2010-10-15
Have been using Ubuntu for 18 months now - its great.
Just added a second PC - both hard wired to a wireless router.
Have been trying to use NFS to share files with no result.

I want to share all files in "home" on PC called "Dimension"

Can anyone talk me through this?

---

### Post by SeijiSensei on 2010-10-15
Can you tell us what you've tried?  Specifically, have you installed nfs-kernel-server on Dimension and created an entry in /etc/exports for /home?  Did you restart the server?

---

### Post by bill-lancaster on 2010-10-15
On the Dimension PC,
1) edited /etc/exports to add info re folder to export
2) ran nfs-kernel restart
3) hadn't installed nfs-kernel so installed it
4) Changed name of PC to "Dimension" to avoid conflict with other PC
5) edited /etc/exports to contain "Dimension:home /MountPoint rw,sync,no_root_squash"
6) ran nfs-kernel restart again, get message:-

 * Stopping NFS kernel daemon                                                   
Warning: Fake start-stop-daemon called, doing nothing.

Warning: Fake start-stop-daemon called, doing nothing.
                                                                         [ OK ]
 * Unexporting directories for NFS kernel daemon...                      [ OK ] 
 * Exporting directories for NFS kernel daemon...                               exportfs: No options for /bill(rw,async,all_squash) : suggest (sync) to avoid warning
exportfs: /etc/exports [1]: Neither 'subtree_check' or 'no_subtree_check' specified for export ":/bill(rw,async,all_squash)".
  Assuming default behaviour ('no_subtree_check').
  NOTE: this default has changed since nfs-utils version 1.0.x

exportfs: Warning: /bill(rw,async,all_squash) does not exist
                                                                         [ OK ]
 * Starting NFS kernel daemon                                                   
Warning: Fake start-stop-daemon called, doing nothing.

Warning: Fake start-stop-daemon called, doing nothing.

Clearly, I don't know what I'm doing wrong, can you help?

---

### Post by SeijiSensei on 2010-10-15
/etc/exports should look like this:
```

/home              192.168.1.0/24(rw,sync,no_root_squash)

```
to export the /home directory to the 192.168.1.0/24 network.  Just replace that with a different network address if you're using something else.  If you're trying to export to only one specific machine named "bill", you'll need entries in /etc/hosts on both machines.  If you want to refer to the server as "dimension", you'll need entries for it as well.  I think it's easier just to use network addresses myself.  

Supposing that you have an entry in the client's /etc/hosts for "dimension" you should now be able to do the following on the client:
```

sudo mkdir /media/dimension
sudo mount dimension:/home /media/dimension

```

I've found "sync" to slow down NFS transfers considerably, so I usually replace "sync" with "async" among the options in /etc/exports.  You might lose data if the server were to crash during a file transfer, but that's a pretty unlikely event.

You can restart the NFS server with "sudo service nfs-kernel-server restart".

---

### Post by bill-lancaster on 2010-10-16
OK, Dimension PC /etc/export  has

"/home  192.168.1.0/24(rw,async,no_root_squash"

I ran "sudo /etc/init.d/nfs-kernel-server restart" and got a similar message to last time:-

" * Stopping NFS kernel daemon                                                   
Warning: Fake start-stop-daemon called, doing nothing.

Warning: Fake start-stop-daemon called, doing nothing.
                                                                         [ OK ]
 * Unexporting directories for NFS kernel daemon...                      [ OK ] 
 * Exporting directories for NFS kernel daemon...                               exportfs: No options for /bill(rw,async,all_squash) : suggest (sync) to avoid warning
exportfs: /etc/exports [1]: Neither 'subtree_check' or 'no_subtree_check' specified for export ":/bill(rw,async,all_squash)".
  Assuming default behaviour ('no_subtree_check').
  NOTE: this default has changed since nfs-utils version 1.0.x

exportfs: Warning: /bill(rw,async,all_squash) does not exist
                                                                         [ OK ]
 * Starting NFS kernel daemon                                                   
Warning: Fake start-stop-daemon called, doing nothing.

Warning: Fake start-stop-daemon called, doing nothing."

The created /media/dimension on the other PC ("Ubuntu")

Then "sudo mount dimension:/home /media/dimension" produced

"DNS resoltion failed for Dimension:  no address associated with host name"

Am mystified with the line "exportfs: Warning: /bill(rw,async,all_squash) does not exist" when server restarted on Dimension

---

