---
title: "Difficulties to expect with getting a graphics card - ?"
date: 2015-02-24
forum: Multimedia Software
---

### Post by michael-piziak on 2015-02-24
I'm about to pull the trigger on a [COLOR=#000000]nVidia GT 610 video card for my older computer.

What difficulties might I expect after I install it.

Will I have to adjust something in the Bios ?

Will I need to install driver(s) ?  Hopefully from the software center if so.

For reference this is my computer: [/COLOR]http://deit.desales.edu/deit/assets/dc5800_data_sheet.pdf[COLOR=#000000]


[/COLOR]

---

### Post by Bucky Ball on 2015-02-25
*Thread moved to **Multimedia**.*

From what I can glean from a thirty second search on the net you need to install nvidia-current and nvidia-settings and that should do it. Presuming you're using 14.04 LTS? Please inform.

---

### Post by michael-piziak on 2015-02-25
> **Bucky Ball said:**
> *Thread moved to **Multimedia**.*

From what I can glean from a thirty second search on the net you need to install nvidia-current and nvidia-settings and that should do it. Presuming you're using 14.04 LTS? Please inform.

I'm running Ubuntu 12.04 LTS.

Are those two things to install available in the software center?   I see something with nvidia current in there, but not the other.

Or perhaps they can both be fetched by going to "Additional Drivers" - ?

---

### Post by oldfred on 2015-02-25
I have the GT610 and before that 9600GT.

I was going to buy a new video card for my new build, but wanted to see how well the Intel internal video worked so did not buy it. But I bought the wrong version of the mother board and it did not have matching video connectors for my monitor, so I had to plug in the "GT610 to have Digital out that I needed. The open source video has worked with 14.04 without issues. I have yet to intall the nVidia driver as I still want to test Intel vs. nVidia, but need a new cable, system works well, and it is up against the wall so not easy to change.

If the 12.04 has the older open source drivers, you may need nomodeset to boot. I always had to use nomodeset with 12.04 and my 9600GT. Then I normally installed nvidia-current from system settings. In 12.04 you have an icon for drivers, but in 14.04 that is a tab under additional software icon in system settings.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

            Installer BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

If not reinstalling and you need nomodeset, then just edit grub when you boot until you install the nvidia drivers.

Only install from repository. You do not need to download from nVidia and compile, nor use a ppa for a newer driver. Many older cards now need legacy drivers and version varies by card. You should be able to just install the newest from the repository.


 nVidia driver versions:
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)
Legacy drivers by GPU model 
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)

---

### Post by michael-piziak on 2015-02-25
> **oldfred said:**
> I have the GT610 and before that 9600GT.

I was going to buy a new video card for my new build, but wanted to see how well the Intel internal video worked so did not buy it. But I bought the wrong version of the mother board and it did not have matching video connectors for my monitor, so I had to plug in the "GT610 to have Digital out that I needed. The open source video has worked with 14.04 without issues. I have yet to intall the nVidia driver as I still want to test Intel vs. nVidia, but need a new cable, system works well, and it is up against the wall so not easy to change.

If the 12.04 has the older open source drivers, you may need nomodeset to boot. I always had to use nomodeset with 12.04 and my 9600GT. Then I normally installed nvidia-current from system settings. In 12.04 you have an icon for drivers, but in 14.04 that is a tab under additional software icon in system settings.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

            Installer BIOS screens shown
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

If not reinstalling and you need nomodeset, then just edit grub when you boot until you install the nvidia drivers.

Only install from repository. You do not need to download from nVidia and compile, nor use a ppa for a newer driver. Many older cards now need legacy drivers and version varies by card. You should be able to just install the newest from the repository.


 nVidia driver versions:
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)
Legacy drivers by GPU model 
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)

Thanks for taking the time to make such a detailed reply.  If you could simplify those instructions a bit and tell me a few things to try first I'd appreciate it.

I'm going to back everything up just in case I can't pull this off.  I was hoping I could install the card, then go to "additional drivers" and see if it would install the drivers for the card, and if it didn't work yet, then go to Software Center and install Nvidia driver (the current one).

You mentioned reinstall.  If I reinstalled 12.04 lts, would it pick up on the card ?  It's not hard for me to do a reinstall as I have my folders backed up.

---

### Post by The Cog on 2015-02-25
If you can find the software and updates settings, look in the additional drivers tab. Shot of mine attached. 
My only problem was that with the nvidia drivers, the PC crashed a few seconds after starting to play games. It took me ages to figure out it was the power supply unable to cope when the graphics card was working hard. New PSU and it's lovely.

---

### Post by oldfred on 2015-02-25
Either first boot or first boot after an install with the new nVidia card, you need the nomodeset. Details are in the links, but it is just as described on edit grub. If you only have Ubuntu you have to press shift key from BIOS until grub menu appears.

---

### Post by michael-piziak on 2015-02-25
> **The Cog said:**
> If you can find the software and updates settings, look in the additional drivers tab. Shot of mine attached. 
My only problem was that with the nvidia drivers, the PC crashed a few seconds after starting to play games. It took me ages to figure out it was the power supply unable to cope when the graphics card was working hard. New PSU and it's lovely.

In 12.04 LTS I don't think there is an additional drivers tab in software and updates.

However, there is an "additional drivers" program in Dash Home.

See 2 attached screen shots.

Updating Reply.

> **oldfred said:**
> Either first boot or first boot after an install with the new nVidia card, you need the nomodeset. Details are in the links, but it is just as described on edit grub. If you only have Ubuntu you have to press shift key from BIOS until grub menu appears.

ok, I figured out how to get to grub on my system.  I am practicing to do this nomodeset before I get the card - which has been ordered.

I booted into grub.  I hit e and the following screen comes up.

It looks like I will manually type and edit/change the screen.

Please tell me exactly what I'll need to do or type.

See attached screenshot (taken with my camera).

---

### Post by Bucky Ball on 2015-02-25
At the end of the line that ends with 'splash', make that last bit look like this:

```
quiet splash nomodeset
```

That's it.

---

### Post by michael-piziak on 2015-02-25
> **Bucky Ball said:**
> At the end of the line that ends with 'splash', make that last bit look like this:

```
quiet splash nomodeset
```

That's it.

To be crystal clear,  I change this line:

Linux /boot/vmlinuz-3.13.0-46-genericroot=UUID=4b592262-7c6e-48ab-82cf-db2d0eefd525 ro    quiet splash$vt_handoff

to this:


Linux /boot/vmlinuz-3.13.0-46-genericroot=UUID=4b592262-7c6e-48ab-82cf-db2d0eefd525 ro    quiet splash nomodeset

right?


Then I assume one hits a key to save the change.


By the way, thanks SO MUCH to all of you for helping me with this.  This is helping me figure out what to do before the card arrives.

---

### Post by oldfred on 2015-02-25
It is not a saved entry, and you should not have to save it. 
Instructions on the grub edit menu say what options to either boot or return to menu or command line.
But if you do not add nVidia driver, you will have to add it again until you do install driver. 
Again nomodeset many not be required.

I typically replace quiet splash, just to see all the commands scroll by. Then I know it still is booting or perhaps see an error if it stops.

---

### Post by michael-piziak on 2015-02-25
> **oldfred said:**
> It is not a saved entry, and you should not have to save it. 
Instructions on the grub edit menu say what options to either boot or return to menu or command line.
But if you do not add nVidia driver, you will have to add it again until you do install driver. 
Again nomodeset many not be required.

I typically replace quiet splash, just to see all the commands scroll by. Then I know it still is booting or perhaps see an error if it stops.


ok, so I simply edit that grub menu line like I typed before and choose boot.  I'll wait to do this after the first boot to see if it needs done as you said.

As far as adding the nVidia driver, that isn't done in Grub (right?).  I have to go to the Ubuntu Software center, or click the icon "Additional Drivers" to get that - right ?

Thanks again for all the help.  I want to be clear on what to do when I start this process and your help is making it clear for me.

OK.  I understand the "[COLOR=#000000][FONT=Ubuntu Mono]nomodeset"  part.  But where to go from here ?[/FONT][/COLOR]

As the video card will be here Friday, I am wondering what the best approach is to install the driver for it once I get it in the machine.

Should I click on "Additional Drivers" and see if Ubuntu can find drivers for it?

Should I download the Nvidia software in the software center?   [I see many unsatisfactory comments left under *Nvida binary X.org driver (current driver)* in the software center].

Should I follow the instructions in the youtube video in this thread:  [http://ubuntuforums.org/showthread.php?t=2049448](http://ubuntuforums.org/showthread.php?t=2049448)                  ?

Should I seek out command lines to input into terminal like those found on this page: [http://www.noobslab.com/2012/10/install-latest-nvidia-drivers-in-ubuntu.html](http://www.noobslab.com/2012/10/install-latest-nvidia-drivers-in-ubuntu.html)

I have read not to get the drivers from the Nvidia website.

So again, where to go from here?

---

### Post by oldfred on 2015-02-25
As we have posted several times above, you need to use System settings.
It should look like this, but actual screen shot is from 14.04, but with 12.04 it will be very similar.

---

### Post by michael-piziak on 2015-02-25
> **oldfred said:**
> As we have posted several times above, you need to use System settings.
It should look like this, but actual screen shot is from 14.04, but with 12.04 it will be very similar.

Thanks for your reply.

12.04 LTS doesn't have that tab.  So I assume I will just use the icon "Additional Drivers" to achieve the same result.

---

### Post by Bucky Ball on 2015-02-26
> **michael-piziak said:**
> So I assume I will just use the icon "Additional Drivers" to achieve the same result.

Yep. Your second pic. As you'll notice from oldfred's pic, he is open at the 'Additional Drivers' tab in 14.04.

---

### Post by michael-piziak on 2015-02-26
Thanks so much everyone.  I very much appreciate all your help!

I get the card tomorrow.

Marking this thread as solved.  If I have problems tomorrow, I'll start a new thread.

---

### Post by Bucky Ball on 2015-02-26
Good luck with it. One more sleep! ;)

---

