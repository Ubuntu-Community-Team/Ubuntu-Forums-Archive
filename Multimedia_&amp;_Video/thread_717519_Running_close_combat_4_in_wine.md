---
title: "Running close combat 4 in wine"
date: 2008-03-07
forum: Multimedia &amp; Video
---

### Post by salviablue on 2008-03-07
Hi, I have been trying to get close combat 4 to work in wine. I have read about the place that it is possible but cannot find any tutorials and all my tinkering hasn`t been able to do it.
 I have gotten past the "close combat has encountered an internal error at address blah blah and will now close" by running it in a virtual desktop. But now it says it "unable to initialize multimedia stream" and I cant seem to find a way around this. I have tried running wine in different windows compat versions to no avail. 
  Any help would be fantastic please!!!!!

Here is the command line output when trying to run the game.

> Xlib:  extension "XFree86-DRI" missing on display ":1.0".
ALSA lib conf.c:3952:(snd_config_expand) Unknown parameters 0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL default:0
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
fixme:win:EnumDisplayDevicesW ((null),0,0x34f768,0x00000000), stub!
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x13ac38)->(0x20024,00000013)
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:d3d:IWineD3DClipperImpl_SetClipList (0x17d000,0x9336a0,0),stub!
fixme:d3d:IWineD3DClipperImpl_SetClipList (0x17d000,(nil),0),stub!
fixme:amstream:IAMMultiMediaStreamImpl_QueryInterface (0x184f48/0x184f48)->({bebe595c-9a6f-11d0-8fde-00c04fd9189d},0x5daa70)
fixme:amstream:IAMMultiMediaStreamImpl_Initialize (0x184f48/0x184f48)->(0,0,(nil)) partial stub!
err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"quartz.dll"
err:ole:CoGetClassObject no class object {e436ebb3-524f-11ce-9f53-0020af0ba770} could be created for context 0x1



                                                                           
I used to play the close combat games constantly in windows, I lost the cd (with a load of others) but have recenty re-aquired them. I no longer have a windows partition to run them in.

---

### Post by salviablue on 2008-03-07
Right, I have just got around that, I am now stuck on 
"unable to get vid interface"
??
cmd line output, minus the debugging stuff. Ill post it if its needed.

I will also update how i got around the prev prob as soon as i get back (i`m going out now!)

> Xlib:  extension "XFree86-DRI" missing on display ":1.0".
ALSA lib conf.c:3952:(snd_config_expand) Unknown parameters 0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL default:0
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
fixme:win:EnumDisplayDevicesW ((null),0,0x34f768,0x00000000), stub!
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x13ac38)->(0x20024,00000013)
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:d3d:IWineD3DClipperImpl_SetClipList (0x17d000,0x9336a0,0),stub!
fixme:d3d:IWineD3DClipperImpl_SetClipList (0x17d000,(nil),0),stub!
fixme:amstream:IAMMultiMediaStreamImpl_QueryInterface (0x184f60/0x184f60)->({bebe595c-9a6f-11d0-8fde-00c04fd9189d},0x5daa70)
fixme:amstream:IAMMultiMediaStreamImpl_Initialize (0x184f60/0x184f60)->(0,0,(nil)) partial stub!
fixme:amstream:IAMMultiMediaStreamImpl_AddMediaStream (0x184f60/0x184f60)->(0x13ac48,0x51a768,0,0x5daa74) partial stub!
fixme:amstream:IAMMultiMediaStreamImpl_AddMediaStream (0x184f60/0x184f60)->((nil),0x51a758,1,(nil)) partial stub!
err:amstream:IMediaStreamImpl_QueryInterface (0x1883b8)->({f4104fce-9a70-11d0-8fde-00c04fd9189d},0x5daa78),not found
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x13ac38)->((nil),00000008)
wine: Unhandled page fault on read access to 0x00000000 at address (nil) (thread 0009), starting debugger...
Unhandled exception: page fault on read access to 0x00000000 in 32-bit code (0x00000000).
Register dump:


Please, anyone!?!?!?

---

### Post by Talorgan on 2008-03-08
First post here.

Don't know if you've seen these posts:

[http://www.closecombatseries.net/CCS/modules.php?name=Forums&file=viewtopic&t=3400&highlight=vmware](http://www.closecombatseries.net/CCS/modules.php?name=Forums&file=viewtopic&t=3400&highlight=vmware)

[http://www.closecombatseries.net/CCS/modules.php?name=Forums&file=viewtopic&t=3254&highlight=vmware](http://www.closecombatseries.net/CCS/modules.php?name=Forums&file=viewtopic&t=3254&highlight=vmware)

It's looking as if VMWare is going to be the way to do it, but nobody has sat down and written a step-by-step "HowTo" yet.

Hope this helps.

Cheers!

---

### Post by salviablue on 2008-03-09
Yes, thankyou anyway. vmware was actually going to be the next step! I was hoping to be able to fullyget to grips with wine first before having to learn a new prog, but nevermind, the whole linux experience has been a bit of a jump into the deep end. Thanks for the reply anyway.

---

### Post by Talorgan on 2008-03-10
I hasten to add that I haven't actually set up VMWare myself. Like you, I'm up to my neck at the deep end with other aspects of this Ubuntu experience. I'm glad I've made the jump though. Every new "Windows Genuine Advantage" just renews my determination.

---

### Post by salviablue on 2008-03-13
Right, I have VMware installed and have setup a virtual win2000 (I was going to set up 98 but my cd is too old and knackered and I have only 2000 and xp cd`s) xp too big to install just for a couple of old games the only trouble is that CC series wont run on win post win 98 with out a patch. So currently i am struggling with setting up ethernet/loopback connection, or a shared drive, so i can copy the patch onto the guest (win2000) and get CCIV working! 
  I too am more and more convinced the linux jump was the right thing to do everytime my friends have new gripes with windows restrictions when I am constantly finding more and more flexability with ubuntu!

---

### Post by Talorgan on 2008-03-16
> **salviablue said:**
> the only trouble is that CC series wont run on win post win 98 with out a patch

They run fine on XP; the problems are with W2K and Vista.

> **salviablue said:**
> I too am more and more convinced the linux jump was the right thing to do everytime my friends have new gripes with windows restrictions when I am constantly finding more and more flexability with ubuntu!

Me too. Have just spent the weekend learning new tricks on Ubuntu. Not quite ready to ditch Windows but progress is definitely being made.

---

### Post by Talorgan on 2008-04-06
Well, I tried to post all the pretty picture here, but the system wouldn't let me.

So, you'll have to settle for a link:

[http://www.closecombatseries.net/CCS/modules.php?name=Forums&file=viewtopic&t=3400](http://www.closecombatseries.net/CCS/modules.php?name=Forums&file=viewtopic&t=3400)

---

