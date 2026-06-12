---
title: "livestation no video"
date: 2009-04-28
forum: Multimedia Software
---

### Post by broecher on 2009-04-28
Hello,

I just upgraded to Jaunty from hardy. Livestation was working well enough in hardy but now  in jaunty when I open it i get audio on the default station but no video. The desktop completely freezes and i have to do a hard restart to get out.

I did try to reinstall both jaunty and livestation. No luck. Below is my display hardware/driver info.

I don't know if this is related but when I tried to turn on my backspace desktop restart function, terminal acted like it worked, but when I tried to close terminal it warned me that something was in progress. It did this for something else also. It never did actually complete. (Livestation didn't work before running any unsuccessful programs in terminal)

I am back on hardy for now -  I sure miss the 70 second start time!!

Thanks!




*-display
             description: VGA compatible controller
             product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list
             configuration: driver=i810_smbus latency=0 module=i2c_i810

---

### Post by Rich-NJ on 2009-05-03
[SIZE=3][COLOR=SeaGreen]Hello,

I had some of the same problems.  I have just upgraded to the most recent version of Ubuntu.  I have discovered today that on my computer (I click on System, Administration, and Hardware Drivers) I had to install NVIDIA drivers in order for video to work.  Hope this helps.

Rich[/COLOR][/SIZE][SIZE=3]
[/SIZE]

---

### Post by broecher on 2009-05-04
Thanks Rich. So you have a nvidia video card. I have an intel card which I thought had open-source drivers. I did find an old driver download for my card for Linux, but I don't know what to do to install it. Do you remember what you did to install yours? It came as an archive folder with 7 sub-folders and 4 loose files.

Also, are you saying you couldn't get livestation specifically to work or just had other video problems. I notice my visual effects are stuck on 'none'.

---

### Post by broecher on 2009-05-04
Rich:

PS

I figured out why I couldn't get out of terminal, after entering sudo mode you have to type exit, you cant just close the terminal window.

---

### Post by Rich-NJ on 2009-05-05
[SIZE=4][COLOR=Blue]


Hello,

I had the same problem; I had audio, but no video in Livestation.  At first I thought I needed plugins or codecs to make it work.  That helped in the EEE version of Ubuntu, and with Kubuntu.  It seems I have to load the video drivers in the most current version of Ubuntu.  I had used the pull down menu to find the drivers for my computer.  I did not have to go to terminal.  Did you try to go to System then Administration then Hardware Drivers on your computer?  When I did that, I had three choices and I chose what was recommended.  

Rich
[/COLOR][/SIZE]

---

### Post by broecher on 2009-05-05
hmmmm.... my proprietary driver list (system, admin, hardware driver) is blank.

---

### Post by freethinkingfuture on 2009-11-06
Did anyone find a solution to this problem?  I have the same system configuration (9.04), and the exact same problem with my Dell Optiplex GX260 with the onboard Intel 845 video (which is blacklisted).

My problem is just as detailed by another user above.  Livestation opens a video link with "connecting", "connected", the audio starts, but no video, and a few seconds later, the GUI locks up (requiring a hard reset).  The audio still keeps playing, and the mouse still scrolls, but everything else is completely locked up.

Any help would be appreciated.  I know replacing the video card is a likely solution, but it's just not within my budget at this time.  Thanks!

---

