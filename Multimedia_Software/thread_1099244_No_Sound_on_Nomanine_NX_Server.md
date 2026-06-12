---
title: "No Sound on Nomanine NX Server"
date: 2009-03-18
forum: Multimedia Software
---

### Post by tjweaver on 2009-03-18
(title meant to say nomachine - sorry)

Hi,

I recently installed Ubuntu 8.10 on a computer hooked up to my stereo with the hopes of using it as a music player.  I am using NoMachine NX free server (most current addition) and NoMachine client on a winxp computer.

When I login to the Ubuntu machine locally sound card shows up properly and the sound works just fine.  When I reboot the Ubuntu system and do not login locally and then connect and login over NoMachine there is no sound on the server.

The volume bar has a red x over it and i get the g-streamer message that the volume control did not find any elements and/or devices to control.

If I reboot the computer, login locally and stay logged in, then login over Nomachine the sound is just fine.  So somehow the sound components are being initialized when I login locally but not remotely.  Also, it is the same user acct and pwd used for local login and remote NoMachine login.

Just to clarify. I am not trying to play audio from the server onto the client over ESD. I simply want to be able to play audio files on the server (that is hooked up to a home stereo) and control the audio playback with the client.

My system: P4 2.4 ghz
OS - Linux Mint 6 w/ Gnome
Audio Card: Aureon 7.1 Universe (Mint identifies the card correctly)
[ALSA details on the card: http://www.alsa-project.org/main/index.php/Matrix:Module-ice1724]("ALSA details on the card: http://www.alsa-project.org/main/index.php/Matrix:Module-ice1724")
nomachine client: winxp

I do not think it is the sound card itself because i've been able to reproduce this issue on another computer using vm.

Any help would be appreciated.  I posted this question a couple days ago in the linux mint forum thinking it was a mint issue (I was trying mint out).  Getting no replies I decided to switch back to Ubuntu this time from 8.04 to 8.10 and got the problem again.  I do not have this issue on 8.04  So it is looking like an 8.10 issue.  I was using Mint 6 which i based on 8.10.  Also I tried doing this with freenx server and had the same problem.

Thanks for your time.

---

### Post by tjweaver on 2009-03-18
Hi,

Would this be more appropriately posted in the network forum?  If so, is it possible to move it w/o a double post?

Thanks

---

### Post by stephanunc on 2010-02-19
I have the same problem. I have the console session playing music as my media center. Then I log in with NX Client (multimedia support disabled) and it takes over the sound on the computer. I would prefer it to control no sound at all and leave the control with the console session. 

Did you figure this out? 

Thanks!

---

