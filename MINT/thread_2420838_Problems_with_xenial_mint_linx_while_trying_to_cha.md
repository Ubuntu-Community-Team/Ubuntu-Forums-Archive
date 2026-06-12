---
title: "Problems with xenial mint linx while trying to charge and mount iPad mini."
date: 2019-06-11
forum: MINT
---

### Post by info19 on 2019-06-11
Hi,

Newbie here.

When i type:

[HTML]sudo apt-add-repository ppa:heathbar/ipad-charge[/HTML]

i get a message in the terminal:

[HTML]'This PPA does not support xenial'
Cannot add PPA: ''This PPA does not support xenial''[/HTML]

I have typed something in that brought up the gedit xenial file and i messed with it.

Then i typed something else in to fix it and now it just doesn't work.

If i can do any diagnostics for you to help me please let me know.

Any help very apprieciated.

---

### Post by howefield on 2019-06-11
Thread moved to the "*MINT*" forum.

---

### Post by yancek on 2019-06-11
Try the link below which shows a version for xenial.

[https://www.ubuntuupdates.org/pm/ipad-charge](https://www.ubuntuupdates.org/pm/ipad-charge)

---

### Post by info19 on 2019-06-12
Thanks yancek.

I followed your link. Then clicked the xenial link.

When i click 

[HTML]apt[/HTML]

i get:

[HTML]Software index is broken

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.
[/HTML]

when i click

[HTML]64-bit deb package[/HTML]

i get a similar message saying:

[HTML]Broken dependecies ... try gksudo synaptic or sudo apt-get install -f[/HTML]

which just leads to:

[HTML](synaptic:4438): Gtk-CRITICAL **: gtk_widget_hide: assertion 'GTK_IS_WIDGET (widget)' failed[/HTML]


Any help much appreciated***.***

---

### Post by yancek on 2019-06-13
Did you run sudo apt-get update and sudo apt-get install -f?  What were the results?  Post the contents of the /etc/apt/sources.list file.

---

### Post by info19 on 2019-06-16
I get:

[HTML]
 sudo apt-get install -f
[sudo] password for computer: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  anjuta-common gtkpod-data libanjuta-3-0 libdbus-glib1.0-cil libdbus1.0-cil
  libgdata2.1-cil libgdl-3-5 libgdl-3-common libgkeyfile1.0-cil
  libgtk-sharp-beans-cil libgudev1.0-cil libllvm5.0 libllvm5.0:i386
  libmono-data-tds4.0-cil libmono-system-data4.0-cil
  libmono-system-enterpriseservices4.0-cil libmono-system-numerics4.0-cil
  libmono-system-runtime-serialization4.0-cil
  libmono-system-servicemodel-internals0.0-cil
  libmono-system-transactions4.0-cil libmono-system-xml-linq4.0-cil
  libmono-zeroconf1.0-cil libnewtonsoft-json5.0-cil libnotify0.4-cil
  libtaglib2.1-cil puredata-dev puredata-doc puredata-utils python-bunch
  python-kitchen
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  libgpod4-nogtk
The following NEW packages will be installed
  libgpod4-nogtk
0 to upgrade, 1 to newly install, 0 to remove and 270 not to upgrade.
Need to get 98.7 kB of archives.
After this operation, 337 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://archive.ubuntu.com/ubuntu xenial/main amd64 libgpod4-nogtk amd64 0.8.3-6ubuntu2 [98.7 kB]
Fetched 98.7 kB in 3s (30.8 kB/s)         
Selecting previously unselected package libgpod4-nogtk:amd64.
(Reading database ... 324128 files and directories currently installed.)
Preparing to unpack .../libgpod4-nogtk_0.8.3-6ubuntu2_amd64.deb ...
Unpacking libgpod4-nogtk:amd64 (0.8.3-6ubuntu2) ...
Processing triggers for libc-bin (2.23-0ubuntu11) ...
Setting up libgpod4-nogtk:amd64 (0.8.3-6ubuntu2) ...
Processing triggers for libc-bin (2.23-0ubuntu11) ...[/HTML]

Then listing the contents of the sources file i found a bit tricky as a newbie. I know hoe to change directories but the [HTML]cat[/HTML] command is all I could find for listing the contents of a file.

Let me know exactly what I should type while in [HTML]/etc/apt/[/HTML]

[HTML]cat sources.list
#deb cdrom:[Linux Mint 18.1 _Serena_ - Release amd64 20161213]/ xenial contrib main non-free[/HTML]

Thanks for your ongoing support.

---

### Post by yancek on 2019-06-17
Your output above shows:  "Use 'sudo apt autoremove' to remove them" so run that command.

To show the output of the sources.list, run the command with the full path.  YOu can also use a text editor rather than cat if you wish.

```
cat /etc/apt/sources.list
```

---

### Post by info19 on 2019-06-18
I used Gedit to open 

[HTML]/etc/apt/sources.list[/HTML]

and it returns this:

[HTML]#deb cdrom:[Linux Mint 18.1 _Serena_ - Release amd64 20161213]/ xenial contrib main non-free[/HTML]

---

### Post by yancek on 2019-06-18
That is not a correct, default sources.list for Xenial.  You need a number of other entries as shown at the askubuntu site at the link below.  Also, did you run sudo apt autoremove?

[https://askubuntu.com/questions/863933/ubuntu-16-04-messed-sources-list](https://askubuntu.com/questions/863933/ubuntu-16-04-messed-sources-list)

---

### Post by info19 on 2019-06-20
I have clicked on that link and copied and pasted the text, removing the  origional line of text that was there before but it just says:

[HTML]Sources.list [read-only]
Could not save the file “/etc/apt/sources.list”.
You do not have the permissions necessairy to save the file. Please  check that you have typed the location correctly and try again.[/HTML]

And i haven't typed:

[HTML]sudo apt autoremove[/HTML]

What exactly will that do?

---

### Post by oldfred on 2019-06-20
You cannot copy Ubuntu's repositories into a Mint install and expect to have a working Mint system.

Some info on Ubuntu repositories, but you need to restore Mint's repository.
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

