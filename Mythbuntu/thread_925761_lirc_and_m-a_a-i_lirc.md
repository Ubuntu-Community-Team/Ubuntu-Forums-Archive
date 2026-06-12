---
title: "lirc and m-a a-i lirc"
date: 2008-09-21
forum: Mythbuntu
---

### Post by Sonthun on 2008-09-21
I'm trying to install a new CommandIR Mini using the script provided by the CommandIR website.  When it hits the point where it runs "m-a a-i lirc" then I get the following result:
```
Updated infos about 1 packages
Getting source for kernel version: 2.6.24-19-generic
Kernel headers available in /usr/src/linux-headers-2.6.24-19-generic
Creating symlink...
apt-get install build-essential 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Done!
unpack 
The source tarball could not be found!
Package lirc-modules-source not installed?
Running "m-a -f get lirc-modules-source" may help.
"/usr/share/modass/packages/default.sh" build KVERS=2.6.24-19-generic KSRC=/usr/src/linux KDREV=2.6.24-19.41 kdist_image
find: /usr/src/modules: No such file or directory

```

After that line it just errors out and goes back to the prompt.  I've tried running the "m-a -f get lirc-modules-source" and it runs just fine, but it doesn't solve the problem.  What can I do to fix this?  Thanks.

---

### Post by Kepesk on 2008-10-15
I've run into the exact same problem under Hardy.  Does anyone have any ideas on this?

---

### Post by Kepesk on 2008-10-16
Okay, I have a bit more information.  As has been stated, the script we're using (found at [http://support.commandir.com/content/view/17/29/](http://support.commandir.com/content/view/17/29/) ) fails on the following command: m-a a-i lirc

The appropriate logs don't show that anything goes wrong when that command is run.  Could it be looking for lirc-modules-source in the wrong place?

I've tried inputting the rest of the commands manually, and skipping that one, but that doesn't result in a working lirc, so clearly that command is critical.  The script was written for Feisty.  Is there anything in Hardy that would prevent this command from working?

Thanks.

---

### Post by Kepesk on 2008-10-16
(duplicate post)

---

### Post by superm1 on 2008-10-16
> **Kepesk said:**
> Okay, I have a bit more information.  As has been stated, the script we're using (found at [http://support.commandir.com/content/view/17/29/](http://support.commandir.com/content/view/17/29/) ) fails on the following command: m-a a-i lirc

The appropriate logs don't show that anything goes wrong when that command is run.  Could it be looking for lirc-modules-source in the wrong place?

I've tried inputting the rest of the commands manually, and skipping that one, but that doesn't result in a working lirc, so clearly that command is critical.  The script was written for Feisty.  Is there anything in Hardy that would prevent this command from working?

Thanks.
Yes:

Hardy used DKMS for building it's lirc-modules-source over again.  If you are looking for support for the commandir 2 in hardy, try the package on my ppa:
[https://bugs.edge.launchpad.net/~superm1/+archive](https://bugs.edge.launchpad.net/~superm1/+archive)

If that works out well for you, I can just make a commandir ppa until this all in lirc mainline.

---

### Post by Kepesk on 2008-10-16
Thanks a bunch!  But sadly, it didn't work.
I added your hardy archives to my system, and your packages downloaded and installed just fine, but running the script again (slightly modified to work with the new repository) resulted in the exact same error.  And still nothing in the error logs.

And, just to be clear, I'm trying to get a CommandIR-Mini to work, not a CommandIR II.

Thanks for the help!

---

### Post by superm1 on 2008-10-16
> **Kepesk said:**
> Thanks a bunch!  But sadly, it didn't work.
I added your hardy archives to my system, and your packages downloaded and installed just fine, but running the script again (slightly modified to work with the new repository) resulted in the exact same error.  And still nothing in the error logs.

And, just to be clear, I'm trying to get a CommandIR-Mini to work, not a CommandIR II.

Thanks for the help!
That script is intended for feisty, and a lot has changed since feisty.

The new driver that is in for the command IR 2 also supports the command IR mini afaik.  
If your script is just prepping lirc for the right driver, you should be able to skip that step.

I would recommend you contact the commandir folks and have them update that page for more appropriate directions.

---

### Post by Kepesk on 2008-10-16
It does?  Okay, I didn't realize that.  I'll give the CommandIR II driver a try then.  In the meantime, I did e-mail one of the CommandIR guys this morning (just a few minutes before you responded, in fact), but they don't seem to have any official feedback procedure or even an official support e-mail address, so we'll see what happens.

---

### Post by commandir on 2008-10-16
Hi Jacob, CommandIR Support (me) was off for 3 weeks (got married) so I'll refresh the online docs for the latest versions and make the support email address on the order page easier to see.  Thanks.

---

### Post by Kepesk on 2008-10-16
Thank you!  And congratulations!  I'm sorry I missed your support e-mail address; I didn't intend to give people the wrong idea about your site.

---

### Post by Kepesk on 2008-10-18
Well, I fixed it!

I'll tell you how, but it's a mess, and I wouldn't necessarily recommend it for everyone with this problem

First, I went into Synaptic Package Manager, searched for lirc, and had it do a complete removal of everything with lirc in the name.

Then I opened a terminal and typed

```
sudo find / -name '*lirc*'
```

I then deleted everything with lirc in the name except for the stuff in the kernel header directories.

I then installed the lirc files from superm1's repositories (thanks again, superm1).  I then modified the channel changing script from the commandir page to reflect the proper output.  For me, this involved changing the irsend lines to:

```
irsend -d /dev/lircd1 SEND_ONCE $REMOTE_NAME $digit
```

and

```
irsend -d /dev/lircd1 SEND_ONCE $REMOTE_NAME $cmd
```

And then it worked.  Phew!  If this helps anyone, well then, yay?

---

### Post by commandir on 2008-10-20
Terrific Kepesk!  

Thread FYI: I've updated the MythBuntu instructions to support Ubuntu and Debian (other APT-users) as the new 0.8.4 LIRC release with the new CommandIR userspace driver is still trickling out to the distros:

[http://www.commandir.com/content/view/53/75/](http://www.commandir.com/content/view/53/75/)

---

