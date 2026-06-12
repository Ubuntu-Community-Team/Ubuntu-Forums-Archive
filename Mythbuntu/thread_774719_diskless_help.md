---
title: "diskless help"
date: 2008-04-29
forum: Mythbuntu
---

### Post by the.fubz on 2008-04-29
I followed the instructions for the diskless stuff.  It didn't work.

I want to continue to use DHCP in my DD-WRT router or else none of the other computers will work nor do i want to leave my backend on all the time.

How do I set up the diskless network boot?

---

### Post by laga on 2008-04-29
Please get the updated Mythbuntu Control Centre from the hardy-proposed repository and recreate your diskless image.

Other than that, you'll have to be more specific than "it didn't work".

---

### Post by the.fubz on 2008-04-29
Ok here is the update:

Updated to 0.28 control center and deleted and rebuilt disk image.

followed: [http://www.dd-wrt.com/phpBB2/viewtopic.php?t=4662&highlight=pxe](http://www.dd-wrt.com/phpBB2/viewtopic.php?t=4662&highlight=pxe)

And then you helped me with the following command revision:
dhcp-boot=ltsp/i386/pxelinux.0,,192.168.1.107

Still no results, the network boot never finds anything to load.

Also, in  Opt/ltsp/images the directory is empty... shouldn't there be an image in there?
Also Opt/ltsp/i386 only has folders.

---

### Post by the.fubz on 2008-05-01
bump

---

### Post by laga on 2008-05-02
Hi fubz,

can you try this deb: [http://laga.ath.cx/mythbuntu-control-centre_0.28-0ubuntu1~hardy2_all.deb](http://laga.ath.cx/mythbuntu-control-centre_0.28-0ubuntu1~hardy2_all.deb)

Start mythbuntu-control-centre like this: ```
MCC_DEBUG=true sudo -E /usr/share/mythbuntu-control-centre/bin/mythbuntu-control-centre | tee mcc.log
```

You should now get an error message if it fails. If it doesn't fail and your client still doesn't boot, please post the 'mcc.log' file created by the command line above.

---

### Post by the.fubz on 2008-05-06
I got this "error" after running the command:

/usr/lib/python2.5/site-packages/MythbuntuControlCentre/core.py:172: GtkWarning: Unable to locate theme engine in module_path: "pixmap",
  self.glade = gtk.glade.XML(GLADEDIR + '/' + 'mythbuntu_control_centre.glade')


and the client still did not boot.... so here is the log
[quote="mcc.log"]
Reading package lists... 0%

Reading package lists... 100%

Reading package lists... Done

Building dependency tree... 0%

Building dependency tree... 0%

Building dependency tree... 50%

Building dependency tree... 50%

Building dependency tree

Reading state information... 0%

Reading state information... 0%

Reading state information... Done
[/quote]

---

### Post by the.fubz on 2008-05-08
bump

---

