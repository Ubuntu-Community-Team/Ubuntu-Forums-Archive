---
title: "ATI IXP AC97 controller prob"
date: 2008-07-02
forum: Multimedia Software
---

### Post by shlitz on 2008-07-02
my humble apologies if this is already up but ive been reading and reading and  have yet to figure it out so i decided to post while i continue to read


first time with ubuntu
installed hardy
sound worked then i ran updates and sound no longer works
tried goin into sound stuff under system but no go

laptop gateway mx7525




info i think you need to know based off other posts:


**** List of PLAYBACK Hardware Devices ****


card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Modem [ATI IXP Modem], device 0: ATI IXP MC97 [ATI IXP MC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0





 hwinfo --sound
18: PCI 14.5: 0401 Multimedia audio controller                  
  [Created at pci.296]
  UDI: /org/freedesktop/Hal/devices/pci_1002_4370
  Unique ID: hB6S.6XWGdpUeKe3
  SysFS ID: /devices/pci0000:00/0000:00:14.5
  SysFS BusID: 0000:00:14.5
  Hardware Class: sound
  Model: "Gateway 2000 IXP SB400 AC'97 Audio Controller"
  Vendor: pci 0x1002 "ATI Technologies Inc"
  Device: pci 0x4370 "IXP SB400 AC'97 Audio Controller"
  SubVendor: pci 0x107b "Gateway 2000"
  SubDevice: pci 0x0506 
  Revision: 0x02
  Driver: "ATI IXP AC97 controller"
  Driver Modules: "snd_atiixp"
  Memory Range: 0xc0503400-0xc05034ff (rw,non-prefetchable)
  IRQ: 17 (2131 events)
  Module Alias: "pci:v00001002d00004370sv0000107Bsd00000506bc04sc01i00"
  Driver Info #0:
    Driver Status: snd_atiixp is active
    Driver Activation Cmd: "modprobe snd_atiixp"
  Config Status: cfg=new, avail=yes, need=no, active=unknown




if i need to provide more info let me know what you want

thanks

---

### Post by markbuntu on 2008-07-02
OK, if you go to System/Preferences/Sound in the menu, what does it say you are using for Music and Movies?

---

### Post by shlitz on 2008-07-02
says autodetect


i would think ati ixp ac97 but that doesnt seem to change anything

went ahead and tried every option in the list
no go

---

### Post by markbuntu on 2008-07-02
Ok, right click on the little speaker icon up on the panel and choose Open Volume Control, make sure the sliders are up and there are no red x on the little speaker. 

 In file/change device, which device is chosen?

---

### Post by shlitz on 2008-07-02
line in and mic are muted

pc speakers were muted but i unmuted that a little before i posted
volume is maxed


file>change device:

ati ixp (alsa mixer)    is selected

---

### Post by markbuntu on 2008-07-02
Ok, Change the settings in System/Preferences/Sound to ALSA and the Default Mixer Tracks to ATI IXP (Alsa Mixer)

If that does not help
Go to Applications/Sound and Video and open the Pulse Audio Manager.

What does it say in Server Information:

Default Sink:
Default Source:

---

### Post by shlitz on 2008-07-02
1st step didnt result in anything different

2nd step

pulse audio manager isn't listed

---

### Post by markbuntu on 2008-07-02
Ok, What exactly was updated if you can remember?

If it was a kernel update then try the older kernel from the grub menu.

I have the same AC'97 on board sound and have not had any problems through a zillion updates.

You can get Pulse Audio Manager (paman) with Synaptic. It is really helpful for figuring out sound problems. You chould also get the gnome-alsamixer so you can have a graphic mixer in your menus and asoundconf-gtk to choose your sound card from the menus ( it is in System/Preferences/Default Sound Card after you install it).

Get those and see if you can figure stuff out, they really help a lot.

 If that does not work go here and try this:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

It is sort of long and involved but it does fix sound problems and you will learn a lot about how Ubuntu manages sound. 

If you still have problems come back here. If any of this fixes your problems please tell us what you did and mark this thread as solved with the thread tools.

---

### Post by shlitz on 2008-07-02
ok thanks a lot i appreciate your time

in grub when i select OS:
the newest one ends in 19 - this no sound
the one that ends in 16 - sound is working!!
dont remember full # but im pretty sure you will know what im talking about

gonna get back on the one with no audio and go through all that stuff you listed

ill be sure and post my results

---

### Post by shlitz on 2008-07-02
> You can get Pulse Audio Manager (paman) with Synaptic. It is really helpful for figuring out sound problems. You chould also get the gnome-alsamixer so you can have a graphic mixer in your menus and asoundconf-gtk to choose your sound card from the menus ( it is in System/Preferences/Default Sound Card after you install it).

all i did was download those and install em. reboot with the newest version and my audio is just magically working

pulse audio manager isnt in my application list but audio is working so ill just move along to my other probs


thanks again!

---

### Post by shlitz on 2008-07-03
woke up ready to start knocking out some other issues when i noticed no sound

reboot and hop into the older one and no audio there now either

that link above states it isn't a guide for me given my issue


this smooth transition isn't going so smoothly.
i've rerun through these prior posts with no luck

question to someone if they reply:
should i look into one of the older releases? not sure if its worth it but i need an operational pc. the sound issue is just the tip

---

### Post by guarhunter on 2008-07-10
Try this it just worked for me but that has yet to be seen long term. I can usually restart a few times and my sound will come back, so I don't know if this actually fixed it or not. 

Go to System > Administration > Authorizations 

All of my menus were expanded but if yours are not I went into org > freedesktop > hal > device-access 

In device-access (Scroll down if the menus are expanded it was on the bottom for me)

Click on directly access sound devices, and under the Implicit Authorizations section click edit and set all the drop down boxes to yes. Click Modify. I also did the same for "directly access audio players".

I closed out of it and restarted and my sound worked. Hope this helps you, and I hope it fixes mine for good I've been dealing with this problem ever since I started messing with linux and ubuntu over a year and a half ago. Oh yeah and my gateway is the MX7527 in case anyone else is having the same problem or has found a fix, I'd like to know.

---

### Post by nibsa1242 on 2008-12-23
Been having this problem on my Gateway MX6440 since first update after 8.10 Ibex install. I am trying fixes now and will let you know if I'm able to fix it.

---

### Post by ownsuall on 2009-03-06
Thanks worked for me another mx7527 user

---

### Post by ownsuall on 2009-04-28
Hey i tried doing this on ubuntu 9.04 and it didn't work do you know hot to get it working for 9.04?

---

### Post by nibsa1242 on 2009-04-29
I no longer have issues with 9.04. There was a bug or a series of bugs that were probably responsible for my issues. 

Basically, when Pulse Crashes and you then mute the sound you are muting the sound card itself, not Pulse. When Pulse starts back up, it doesn't unmute the soundcard, so in alsamixer your volume can be all the way up, but the sound hardware itself is muted.

There is a special way to set up alsamixer to deal with the soundhardware directly instead of the soft devices that pulse displays... Check bug reports for more details if you think this is your issue.

---

### Post by ownsuall on 2009-08-16
Got it working in ubuntu 9.04 too used Realtek AC'97 linux audio driver

---

