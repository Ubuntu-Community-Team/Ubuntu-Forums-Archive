---
title: "Internet TV App in 14.04"
date: 2015-07-24
forum: Multimedia Software
---

### Post by coljohnhannibalsmith on 2015-07-24
Hello,

Can anyone recommend a good Internet TV app to use in 14.04?  None of Miro, Me TV, or FreeTux TV work.

Thanks, Hannibal

---

### Post by coljohnhannibalsmith on 2015-07-24
Does anyone know where I can get an Ubuntu TV?

Thanks, Hannibal

---

### Post by bapoumba on 2015-07-24
Threads merged and moved to General Help. The Multimedia Software subforum is for :
> Forum: Multimedia Software

The place for your multimedia software questions: everything about using software for audio, video and image editing, display, or viewing and listening. We also have dedicated sub-forums for Mythbuntu and Ubuntu Studio. All video and sound card, and other hardware inquiries, should go to the Hardware section.

---

### Post by sgian on 2015-07-24
I'm not familiar with the apps you mentioned.  When I watch online videos on Ubuntu 14.04, it is Netflix on Chrome or Amazon Prime on Firefox with HAL installed.

---

### Post by sgian on 2015-07-24
[http://askubuntu.com/questions/459962/freetuxtv-is-installed-in-14-04-and-not-working](http://askubuntu.com/questions/459962/freetuxtv-is-installed-in-14-04-and-not-working) I found this while searching for freetuxtv since it sounded interesting.  For some reason 14.04 isn't listed as supported at [https://apps.ubuntu.com/cat/applications/freetuxtv/](https://apps.ubuntu.com/cat/applications/freetuxtv/)

---

### Post by Bucky Ball on 2015-07-24
If all the apps you mention are not working I'd suggest there is something going on beyond the software side of things. Is your TV card actually recognised? You give no details of what it even is.

If it is USB, reboot the machine with the USB TV dongle out, boot the machine and when at a desktop, plug the dongle in and open a terminal and:

```
dmesg
lsusb
```

Post the output of each command here between code tags, thanks (see last link in my signature).

---

### Post by Bucky Ball on 2015-07-24
If all the apps you mention are not working I'd suggest there is something going on beyond the software side of things. Is your TV card actually recognised? You give no details of what it even is.

If it is USB, reboot the machine with the USB TV dongle out, boot the machine and when at a desktop, plug the dongle in and open a terminal and:

```
dmesg
lsusb
```

Post the output of each command here between code tags, thanks (see last link in my signature).

Posting 'these apps don't work' with no detail about how they don't work, error messages or what you have done to try and fix them gives you very little chance of getting support. See the third link in my signature for tips. :)

---

### Post by coljohnhannibalsmith on 2015-07-24
Bucky Ball,

Thanks for your reply.  None of these apps require a TV card.  They're purely software apps that run on my pc and only require an Internet connection.

I think it's possible that there could be something wrong on the OS side of things; but this is not unique to me.  The reviews say that these programs
constantly crash; but I haven't found an app to try that has a good reputation yet.

Thanks, Hannibal

---

### Post by Bucky Ball on 2015-07-24
??? You need a TV card to run MeTV, or at least to get a picture. Where are you expecting to get the TV signal from? I use MeTV and as far as I know it is not for internet TV.

If the other two aren't working I'd suggest attempting to find out why as whatever that is will probably prevent anything else from working, too.

---

### Post by ajgreeny on 2015-07-24
Are you trying to use a catch-up TV service from one or more of your local TV companies on the web?

IN UK, some of those work reasonably, unfortunately using flash, which has its own difficulties, and others will not work at all, even though they also use flash.

I don't know the applications you mention at all, so can't help with that, but tell us a lot more detail about your comment
> They're purely software apps that run on my pc and only require an Internet connection.and someone may be able to help more than I can.

---

### Post by deadflowr on 2015-07-24
I'd look at kodi (formerly xbmc)
They've got a ton of addons that support various incarnations of LiveTV and Internet streaming services.
Some official, some 3rd party.

[http://kodi.wiki/view/HOW-TO:Install_Kodi_for_Linux](http://kodi.wiki/view/HOW-TO:Install_Kodi_for_Linux)

Be aware that kodi is an all encompassing envirnoment, much like myth.

---

### Post by Bucky Ball on 2015-07-24
> **deadflowr said:**
> I'd look at kodi (formerly xbmc)

Yep. Tons of video/Catch-up TV add-ons. Internet streaming. We use it for hours a day and works great.

---

### Post by coljohnhannibalsmith on 2015-07-24
> **ajgreeny said:**
> Are you trying to use a catch-up TV service from one or more of your local TV companies on the web?

IN UK, some of those work reasonably, unfortunately using flash, which has its own difficulties, and others will not work at all, even though they also use flash.

I don't know the applications you mention at all, so can't help with that, but tell us a lot more detail about your comment
and someone may be able to help more than I can.

This comment was for a poster to this thread that thought I needed a video card.  This was my attempt to explain that I was looking for an app that played streaming content from the web.  This can be either web or live TV.  There are content providers that offer anywhere from several hundred to several thousand channels encoded for web delivery.  Some view this content in their browsers; but I haven't found a suitable plugin for Firefox yet, and it's not a complete solution.  Also some of these players allow broadcasting your own programming from your pc to the web..  Most of these apps however are for Windows.

Thanks, Hannibal

P.S., There's also an app called Ubuntu TV that apparent only runs on 12.04; however the notes say that you can use a virtual machine, which I don't known how to organize.  My other laptop has 12.04, so I might install it there and see how well it works.

[http://www.ubuntu.com/tv](http://www.ubuntu.com/tv)

---

### Post by coljohnhannibalsmith on 2015-07-24
> **deadflowr said:**
> I'd look at kodi (formerly xbmc)

Be aware that kodi is an all encompassing envirnoment, much like myth.

Wow,

kodi looks hot!

I've experimented with Myth in the past and it rebranded my entire OS, which was a very undesirable characteristic; IMHO that made it more appropriate for a dedicated box.  Does kodi do this, or does it simply take over all system resources while it's running, and then release them when exited?  Also, does it need a back-end; and can it be uninstalled without rewriting my OS?

Thanks, Hannibal

---

### Post by blm-ubunet on 2015-07-24
Mythbuntu rebranded your machine not MythTV.

You can use the MythTV packages from mythbuntu without trashing your setup.
You must have installed a mythbuntu meta-package.
There are/were hybrid distributions of kodi/xbmc & ubuntu etc that are best suited to dedicated box.

For broadcast TV Kodi can use mythtv backend or streaming/dlna tuners.

---

### Post by Bucky Ball on 2015-07-24
Kodi doesn't not take over your machine in as much as you still boot to Ubuntu. You can install it and it is just like any other program. Launch Kodi and you're in Kodi and it does take over your machine, but Exit Kodi and your back in Ubuntu. You can swap between one or the other.

Kodi is in Software Centre.

---

### Post by deadflowr on 2015-07-25
Unlike myth, kodi only needs a backend setup if you need to use it.
It'll run fine as a regular media center without one.
(Example watch your dvd or listen to an mp3)

No need to understand things like mysql or mythfilldatabase (or whatever).

Backends can be configured later, at your own leisure.
And your not relegated to having only one option as a backend.
You can try a few if you need.
Here's a few listed that work
[http://kodi.wiki/view/PVR_backend](http://kodi.wiki/view/PVR_backend)

And kodi can be uninstalled without any messing with the overall system.

---

### Post by monkeybrain20122 on 2015-07-25
If you are looking for something like Miro [http://ubuntuforums.org/showthread.php?t=2286343&p=13319189](http://ubuntuforums.org/showthread.php?t=2286343&p=13319189)
The same caveat and disclaimer apply (as Miro)

---

### Post by bapoumba on 2015-07-25
Sorry to have moved the thread around once again, to place it back in Multimedia Software. From the OP it was not clear to me where to put it. The way the discussion has now evolved makes it fit better here than in GH. Hope you do not mind, I'm not that fond of moving thread several times around :)

---

### Post by dino99 on 2015-07-25
Also found into ubuntu archive (fine to review some documents offline)


HTTrack is a free (GPL, libre/free software) and easy-to-use offline browser utility.

It allows you to download a World Wide Web site from the Internet to a local directory, building recursively all directories, getting HTML, images, and other files from the server to your computer. HTTrack arranges the original site's relative link-structure. Simply open a page of the "mirrored" website in your browser, and you can browse the site from link to link, as if you were viewing it online. HTTrack can also update an existing mirrored site, and resume interrupted downloads. HTTrack is fully configurable, and has an integrated help system.

WinHTTrack is the Windows 2000/XP/Vista/Seven release of HTTrack, and WebHTTrack the Linux/Unix/BSD release

---

### Post by coljohnhannibalsmith on 2015-07-25
I've installed kodi and I'm very happy with it.  It doesn't crash, like all of the other apps I've tried.  I do however have a couple of criticisms.
One is that when I enable a channel, the Channels menu will sometimes display the word Enabled on that line, and at other times it won't;
so it's hard to keep track of which channels are enabled.  Also, after I installed kodi, I noticed that the kodi option had been added twice to
the login-menu.  Does anyone know how to edit this?  And, the options for Live TV are almost non-existant, and many are broken; but overall,
this is a very good app; it's fast and responsive, doesn't crash and most of the channels work.

One of the channels requires an N7 tuner.  Does anyone know what this is?  Also, can I broadcast from this app?

Thanks, Hannibal

---

