---
title: "LIRC no multiple / repeat events generated"
date: 2008-05-08
forum: Mythbuntu
---

### Post by rtrevor on 2008-05-08
Hi

I have Mythbuntu 8.04 installed using a Hauppauge Nova-T 500 tuner with the standard remote control that comes with the tuner. The remote control appears to be set up correctly with all buttons mapped and functioning in MythTV and in 'irw', however no repeat events are generated when I hold down a button. Running 'irw' shows only one event is generated no matter how long I hold down the button on the remote.

My ~/.lircrc includes 'repeat 3' for all buttons, but changing this value doesn't seem to make any difference - I suspect this is a config problem lower down the stack as it looks like no repeat events are generated in the first place.

Any suggestions appreciated...

Thanks

---

### Post by ironmongem on 2008-05-13
I have exactly the same problem with Mythbuntu 8.04 and the Nova-T500 remote. I've tried different delay and repeat settings but they have no effect. I know I'm modifying the correct file because I changed some of the button mappings and those changes worked.

I've searched this and other forums, and nobody else seems to be reporting this problem. From what I can gather, support for the Nova-T 500 remote is now in the kernel, so maybe everyone else is using it with an older kernel and lirc.

---

### Post by parc on 2008-05-13
> **ironmongem said:**
> I have exactly the same problem with Mythbuntu 8.04 and the Nova-T500 remote. I've tried different delay and repeat settings but they have no effect. I know I'm modifying the correct file because I changed some of the button mappings and those changes worked.

I've searched this and other forums, and nobody else seems to be reporting this problem. From what I can gather, support for the Nova-T 500 remote is now in the kernel, so maybe everyone else is using it with an older kernel and lirc.

I've the same problem with the MS MCE ir controller ....

---

### Post by oct on 2008-05-18
I'm having the same problem, with the Nova-T 500 remote. I can tell you that the remote itself sends the repeated keypresses when holding down a button, as I can hear the interferences on my guitar amplifier if I use the remote next to my guitar pickups (I found that for a coincidence). It seems that the Nova-T driver takes control of the repeated keys and doesn't allow to pass them to the operating system.
It would be nice to resolve this issue, especially for the volume control.

Oct

---

### Post by SiHa on 2008-08-22
If it helps, I too have the same issue - The Novat card itself seems to filter out the repeat keypresses.

I've just built a remote frontend using a homebrew serial receiver, and irw shows repeated keypresses. In fact it's hard to get just one!

Now if I can just figure out how to get lirc to feed more than one to mythtv!](*,)

---

### Post by oct on 2008-08-25
I think you have to deal with the repeat and delay options in the .lircrc file. This file is a hidden file and is located into your home directory. I don't know exactly how to use this options, as I don't get repeated keypresses from my remote.

About the homebrew receiver, have you built it yourself? Does it work with the Nova T remote? Do you have a guide on how to build it?

Oct

---

### Post by rtrevor on 2008-09-28
I've just upgraded my Mythbuntu box to Intrepid 8.10 and you'll be pleased to know that holding down the buttons on the remote now works!

HOWEVER - lirc seems to have some issues with Xorg at the moment, whereby it cannot get exclusive access to the IR receiver device while Xorg is running. This means that the remote control is effectively useless as it does not register any button presses while Xorg is running.

From a scan through Launchpad it looks like this is the bug, which has just been (incorrectly?) marked as fixed...

[https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/164627](https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/164627)

HTH

---

### Post by rtrevor on 2008-09-28
> **rtrevor said:**
> 
HOWEVER - lirc seems to have some issues with Xorg at the moment, whereby it cannot get exclusive access to the IR receiver device while Xorg is running. This means that the remote control is effectively useless as it does not register any button presses while Xorg is running.

From a scan through Launchpad it looks like this is the bug, which has just been (incorrectly?) marked as fixed...

[https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/164627](https://bugs.launchpad.net/ubuntu/+source/lirc/+bug/164627)


Details for fixing this manually for the Nova-T 500 are now in the bug comments.

---

### Post by SiHa on 2008-09-29
> **oct said:**
> About the homebrew receiver, have you built it yourself? Does it work with the Nova T remote? Do you have a guide on how to build it?

Oct

Hi,

I followed the guide here:
[http://www.lirc.org/receivers.html](http://www.lirc.org/receivers.html)
And built the 'more advanced' version that it links to here:
[http://www.tb-electronic.de/vdr/lirc/lirc_rx.html](http://www.tb-electronic.de/vdr/lirc/lirc_rx.html)

Works beautifully, although I'm not sure T2&T3 are strictly necessary to get a the full +9V/ -9V swing. 

The only problem I had is that Mythbuntu doesn't list the Homebrew Serial as an option when setting up LIRC at install. You have to ```
sudo dpkg-reconfigure lirc
``` after install to configure the serial receiver.

One point to note. The codes received from the Hauppauge remote are completely different using a serial Reciever from the codes received using the inbuilt receiver in the card. You **do** get the repeats though.

**rterevor**: Thanks for the note re: the manual fix. I'll have a look at that later.:)

---

### Post by jb5 on 2008-10-09
> **rtrevor said:**
> Details for fixing this manually for the Nova-T 500 are now in the bug comments.

Just to confirm that the fix mentioned above also works (is necessary?) for intrepid beta1 upgrade, and that multiple events are generated for as long as the remote button is pressed.

---

### Post by SiHa on 2008-10-14
Well, I finally got round to trying the manual fix, and it didn't work for me.

I went to /usr/share/somepathorother/20thirdparty/ and there's no lirc.fdi!

I saved the file linked to in the above bug to to this location, but I still do not get repeat keypresses.

Bah!

---

