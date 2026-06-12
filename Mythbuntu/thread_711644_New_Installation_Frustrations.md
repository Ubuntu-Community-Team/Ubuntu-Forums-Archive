---
title: "New Installation Frustrations"
date: 2008-02-29
forum: Mythbuntu
---

### Post by dlfuller on 2008-02-29
I assembled a computer specifically to try Mythbuntu. ASUS P5K-VM motherboard, 2 MB RAM, Geforce 8500 video, 320 GB hard disk, etc.

A CRT TV is connected with S-Video and my plan was to try a standard default Mythbuntu installation to see how it works before adding a tuner, sound card, remote, and other components to round out a finished setup. The only input I have now to experiment with is Firewire from a Verizon FiOS Motorola QIP 6416-2.

The installation routine sorta went along following the Installation Manual. I choose the nVidia Proprietrary Driver (Geforce 5+), S-Video out, and NTSC-M.

The 640 x 480 TV screen displays the BIOS and startup windows reasonable well with little overscan. But not so in Mythbuntu where windows are cut off due to increased overscan.

Any attempt to resize and reposition the TV windows has been a problem. Any GUI width or height values other than 0 produce a smaller window of about 2/3 full-screen size when using Utilities/Setup > Setup > Appearance to attempt resizing and repositioning. X and Y offset values do seem to work but the TV window remains either oversize or at the smaller 2/3 size.

Is this the right approach to resize the TV window? What is the procedure to input new dimensions? 

Then there is selecting inputs. I was trying to see what video was available from my Firewire input. Firewire was added as an input device, but afterwards any attempt to view using the Watch TV button brings up a "MythTV already using all available inputs for the channel you selected" dialog. I haven't done anything in the area of recording. There were none scheduled or stored.

I used sudo plugreport to check Firewire and had a Node 0 and Node 1 listed. Node 1 had data similar to what's shown in the MythTV Firewire Documentation. That seemed encouraging.

I can play a DVD using MPlayer, etc., with a reasonable picture on the TV. But nothing shows from any play attempts in Mythbuntu. The screen returns right back to the menu after activating the Play button.

What is happening with these inputs? Troubleshooting clues please.

During any shutdown a "LIBC not configured" message appears, but I had bypassed the setup of a remote in the Configure Remote Control window by not checking the box.

Is this LIBC message abnormal?

I'm getting very frustrated from these installation problems. Any suggestions about what I should do next would sure be appreciated. Or, should I just head back to my Mac?

Thanks for your comments.

---

### Post by majoridiot on 2008-02-29
> **dlfuller said:**
> Is this the right approach to resize the TV window? What is the procedure to input new dimensions? 

you should use nvidia-settings to adjust your screen resolution, tv-out, etc.  you will find a launcher for it in
system-->mythbuntu control centre under "proprietary drivers".


> **dlfuller said:**
> Then there is selecting inputs. I was trying to see what video was available from my Firewire input. Firewire was added as an input device, but afterwards any attempt to view using the Watch TV button brings up a "MythTV already using all available inputs for the channel you selected" dialog. I haven't done anything in the area of recording. There were none scheduled or stored.

I used sudo plugreport to check Firewire and had a Node 0 and Node 1 listed. Node 1 had data similar to what's shown in the MythTV Firewire Documentation. That seemed encouraging.

did you follow the firewire guide from start to finish or just check selected bits of it?  i pretty
much guarantee that you will not get a working firewire connection without following all of
the steps from start to finish.

> **dlfuller said:**
> ... should I just head back to my Mac? 

there's no reason to do anything rash, here... ;)

---

### Post by dsbw on 2008-03-01
> **dlfuller said:**
> Then there is selecting inputs. I was trying to see what video was available from my Firewire input. Firewire was added as an input device, but afterwards any attempt to view using the Watch TV button brings up a "MythTV already using all available inputs for the channel you selected" dialog. I haven't done anything in the area of recording. There were none scheduled or stored.

I'm having the exact same problem actually. 

I've gotten MythTV working except with the firewire, where I get the same messages, even though I can capture data off the port directly through test-mpeg2. 

There are a lot of gotchas so you have to be pretty meticulous following the directions, and making sure your STB is tuned to a non-encrypted channel. Any one thing is off, and the whole thing goes to Hades.

---

### Post by majoridiot on 2008-03-01
> **dsbw said:**
> I've gotten MythTV working except with the firewire, where I get the same messages, even though I can capture data off the port directly through test-mpeg2. 

There are a lot of gotchas so you have to be pretty meticulous following the directions, and making sure your STB is tuned to a non-encrypted channel. Any one thing is off, and the whole thing goes to Hades.


VERY meticulous- not *pretty* meticulous... like not skipping steps like giving permission of /dev/raw1394 AND priming, etc.
as pointed out (and hopefully heeded) in the other thread.

you are very right that it doesn't take much for it to go all pear-shaped, which is why that guide covers
the absolute-trust-me-you-gotta-do-this-even-if-you-don't-see-why stuff and skips the *truly* unnecessary bits.

---

### Post by dlfuller on 2008-03-02
Thanks for the comments.  I'm still working through the Firewire steps and the unencrypted channel tip was helpful.  The 6416 did just happen to be on the wrong channel after exiting diagnostic mode.

But I still have other hurdles to deal with first.

Nowhere could I locate any "sliders" to control overscan as mentioned in Overscan on the MythTV Wiki.  The only way I could get the display to fit was to configure the X-server (Xorg Config) to high resolution.  Then using Utilities/Setup > Setup > Appearance and entering some GUI width or height values other than 0 to produce a smaller window.  

Any changes to a lower resolution like 640 x 480 TV resolution would result in giant Mythbuntu windows where the buttons cannot be accessed at the bottom since they are off the screen.

Am I missing a significant point here?  Should I try different drivers than the nVidia (Geforce 8 series) selected during install?

Is there some explanation for the Watch TV button bringing up a "MythTV already using all available inputs for the channel you selected" dialog?  I haven't done anything in the area of recording. There were none scheduled or stored.

The inability to pop at DVD in and play it (Optical Disks > Play DVD) is also a concern.  That would seem to be a simple operation.

Or, should I just wipe the HD and start over with a fresh install if these problems all seem abnormal?  Maybe with Ubuntu 7.10, get stuff working, and then install MythTV or Mythbuntu?

---

### Post by dsbw on 2008-03-03
> **dlfuller said:**
> Am I missing a significant point here?  Should I try different drivers than the nVidia (Geforce 8 series) selected during install?

They are working for me. 

> **dlfuller said:**
> Is there some explanation for the Watch TV button bringing up a "MythTV already using all available inputs for the channel you selected" dialog?  I haven't done anything in the area of recording. There were none scheduled or stored.

It happened to me because: a) I had only one input (firewire); b) the firewire was not set up correctly according to the guide. Therefore, zero channels, therefore "alreadying using all available inputs".

> **dlfuller said:**
> The inability to pop at DVD in and play it (Optical Disks > Play DVD) is also a concern.  That would seem to be a simple operation.

In the Mythbuntu setup panel (the non TV interface one that has buttons like a regular dialog) there's one for proprietary codecs. In there is a checkbox you must select if you want to view commercial DVDs.

---

### Post by dlfuller on 2008-03-03
Thanks dsbw!   Your comments are right on and getting me step-by-step closer to a viable installation by knocking off the "gotchas" one-by-one.

I suspect my install process would have been more straightforward if I had a tuner and a TV connected with something other than S-Video.

A curiosity question.  Did you do (or see) any size changing capability?  Something other than a selection from a list of pre-determined resolutions

---

