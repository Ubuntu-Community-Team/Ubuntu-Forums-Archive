---
title: "remote firefox flash sound using esd"
date: 2008-08-29
forum: Multimedia Software
---

### Post by cad on 2008-08-29
Hello,
I have a linux and a MS-Windows xp box. I run an esd server on my desktop. I want to run youtube on my linux desktop and hear sound on windows. Can someone please list the process how to transfer audio. PLease tell me the environment variables like ESPEAKER and other things. I've tried a *lot* but couldnt find it.
Please note however, that the linux desktop is not under my direct control, i.e. I'm not the root so I can't install any packages.
Thanks

---

### Post by rockin_goliath on 2008-08-29
Since you are not the admin, I can't think of much that you can do. What I would do is to get PulseAudio set up on both machines (yes, there is a windows version, but only in command line form), make the sound devices network discoverable on the Windows machine, set the linux machine to search for network sound devices, then on the linux machine, forward all the audio to the Windows box. I would go about doing this by installing the gui tools in linux (sudo apt-get install pavucontrol pavumeter padevchooser paperfs), but there might be a way to do it all from the command line. If you are using Hardy 8.04, you should already have PulseAudio on the linux box.

I've never done this before, but I know that PulseAudio will allow you to do something like this.

Good luck, and I hope that helps.

---

