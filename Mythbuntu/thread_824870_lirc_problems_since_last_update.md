---
title: "lirc problems since last update"
date: 2008-06-10
forum: Mythbuntu
---

### Post by frego on 2008-06-10
I'm running Mythbuntu 8.04 and am using an MCE remote v.2  (model 1039).  It all worked up until the updates I took today.  Now the remote has stopped working.  Where is the remote config file stored in Mythbuntu?   In my syslog I notice messages like:
Jun 10 11:15:56 mythtv lircd-0.8.3pre1[7448]: config file contains no valid remote control definition

when I restart the lirc service.  So what tells lirc to use a certain config file?

---

### Post by frego on 2008-06-10
More from syslog::
Jun 10 12:56:56 mythtv lircd-0.8.3pre1[13087]: caught signal
Jun 10 12:56:57 mythtv lircd-0.8.3pre1[14303]: error opening child file defined at line 13:
Jun 10 12:56:57 mythtv lircd-0.8.3pre1[14303]: ignoring this child file for now.
Jun 10 12:56:57 mythtv lircd-0.8.3pre1[14303]: config file contains no valid remote control definition
Jun 10 12:56:57 mythtv lircd-0.8.3pre1[14304]: lircd(userspace) ready
Jun 10 12:57:31 mythtv lircd-0.8.3pre1[14304]: caught signal
Jun 10 12:57:31 mythtv lircd-0.8.3pre1[14554]: error opening child file defined at line 13:
Jun 10 12:57:31 mythtv lircd-0.8.3pre1[14554]: ignoring this child file for now.
Jun 10 12:57:31 mythtv lircd-0.8.3pre1[14554]: config file contains no valid remote control definition
Jun 10 12:57:31 mythtv lircd-0.8.3pre1[14555]: lircd(userspace) ready

---

### Post by ian dobson on 2008-06-10
Hi,

I had the same problem with my Homebrew/Hauppage Remote control.

I just copied the /usr/share/lirc/remotes/hauppauge/lircd.conf.hauppauge to /etc/lirc/lircd.conf or was it /etc/lircd.conf and then rebooted.

You'll need to find the correct lircd file for your remote.

Login and do a locate lircd.conf to get a list of all remote configurations available. I think your remote should use:-
/usr/share/lirc/remotes/mceusb/lircd.conf.mceusb

Regards
Ian Dobson

---

### Post by superm1 on 2008-06-10
There were absolutely no changes to remote loading schemes.  Anyone that encounters this, please file a bug as a regression and indicate any changes that you have made to lirc, to conf files, remote selection.  The more information, the easier it will be to solve.

---

### Post by danbodoh on 2008-06-10
When I did an apt-get upgrade today, I noticed that lirc was updated.  After the upgrade, mythfrontend (which was running during the upgrade) would no longer respond to the remote (Hauppauge pvr usb2).

But a simple exit and restart of the frontend solved that problem.

I have noticed in the past the restarting lircd requires a mythfrontend restart before the remote works again.

Dan Bodoh

---

### Post by nrune on 2008-06-10
This update has completely killed my remote.  I am using an xbox usb ir reciever and remote.  The update completely killed my remote in /etc/lircd.conf, it was removed enirely. I have since rebuilt the remote in the file from [http://mythtv.org/wiki/index.php/XBOX_DVD_IR_Receiver](http://mythtv.org/wiki/index.php/XBOX_DVD_IR_Receiver), but the remote is still a no go after reboot.  Any ideas? Help!

---

### Post by ajw107 on 2008-06-10
Hi

I've a similar problem with mythfrontend.  I have a soundgraph imon pad remote, and this all happened since todays' update.  The funny thing is that mPlayer (which I use to play videos on mythTV [although not recordings or DVDs which mythVideo still handles]) works fine.  So this is just a mythTV problem, is something blocking lirc from seeing the right program identifier for mythTV or something?  It's just weird that mplayer works, whereas mythtv doesn't.

---

### Post by nrune on 2008-06-10
Downgrade of package fixed the problem.  Not sure where or how to help report this bug...  let me know and I will report it.

Mike

---

### Post by lubricus on 2008-06-10
I had a similar problem (ir blasting no longer worked) but was able to fix it.

It had been a while since I set this box up so I had forgotten where all the files were, but [this helps a lot]("https://help.ubuntu.com/community/Motorola_DCT700_Channel_Change_Script") (I'm pretty sure it's what I used to set it up in the first place).

The short of it was that I had customized the "name" or my transmitter in my:
```

/usr/share/lirc/transmitters/motorola/dctxxxx.conf
```

file.

The update replaced this file (moved the old one to dctxxx.conf.old), so that my channel change script was pointed to the wrong name...

changing the name in the channel changing script fixed the problem.

```

/usr/bin/change-channel.py

def irsend(button):
   remote = 'DCT2000' #change to the name of your remote from .conf file above

```

---

### Post by frego on 2008-06-11
ian> thanks for the location of that file!  That got me going down the right path.  

Super>  I'm trying to track down what changes I had made that likely caused this to happen during the upgrade of lirc.  I'll submit a bug report if appropriate.  

I have made some progress... lirc starts and stops correctly without leaving any nasty messages in syslog.  Also, irw at least sees the keypresses from my remote.  But for some reason myth still doesn't see them.

---

### Post by ian dobson on 2008-06-11
> **superm1 said:**
> There were absolutely no changes to remote loading schemes.  Anyone that encounters this, please file a bug as a regression and indicate any changes that you have made to lirc, to conf files, remote selection.  The more information, the easier it will be to solve.

The last upgrade replaced my lircd.conf with a version that just contained the text that there is no upgrade supported for generic/homebrew IR and that I should post a bug report.

An I was in a hurry to get the system up and running again I just copied the hauppage config file and rebooted.

Note Running Homebrew/Serial IR with Hauppage 150 remote.

Regards
Ian Dobson

---

### Post by superm1 on 2008-06-11
Ah okay.  You are talking about this bug: [https://bugs.edge.launchpad.net/ubuntu/+source/lirc/+bug/206609](https://bugs.edge.launchpad.net/ubuntu/+source/lirc/+bug/206609)

The current "supported" way to do it, is to set your remote to "Custom" so it's not overwritten.  Eventually this should get fixed in the intrepid packages.

---

### Post by Monsieur Gonzalez on 2008-06-11
Well, I had mine set to "Custom", and it was overwritten. Luckily there's a copy in the same folder, but I think the package should ask before overriding any files.

---

### Post by nrune on 2008-06-11
So how does one make a remote a customized remote?

---

