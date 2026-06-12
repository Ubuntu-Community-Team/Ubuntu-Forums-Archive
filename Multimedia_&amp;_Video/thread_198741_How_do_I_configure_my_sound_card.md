---
title: "How do I configure my sound card?"
date: 2006-06-17
forum: Multimedia &amp; Video
---

### Post by Hyphessobrycon on 2006-06-17
I have an old Aptiva IBM S Series 631 PC which used to be running windows 98 but which I have converted to run Ubuntu. I am extremely new to Ubuntu, so please forgive my ignorance. Whenever I click on the volume control icon in the upper right-hand corner of my screen, it gives me an error dialogue that says "No Volume Control GStreamer plugins and/or devices found." When I go to System-Preferences-Sound, there are no options in the default sound card field. When I try to open the "Movie Player," it gives me a message: "Totem could not start up. Could not establish a connection to the sound server." I am not sure whether Ubuntu is detecting my sound card or not. I did try to search the forum before posting this, and I saw another thread that said that the sound card for his Aptiva was integrated into the mobo. I am not sure whether this applies to my machine, since I think I have a different model than he did. Because of the fact that I don't know what to look for,  this description of my problem may be lacking in information. If there is any further info I can give you, just let me know what it is and preferably, how to find it. Please help, for I have absolutely no idea what to do. Thanks.

---

### Post by yenruoj on 2006-06-20
I have recently upgraded and am experiencing exactly the same issues and error messages with the volume control and Totem -- however, the default CD player works perfectly. :confused:

---

### Post by yeateg on 2006-06-20
Open a concole, change to su, and then type
alsaconf
this will open up the alsa sound card configuration program.  It is now a matter of following the instructions and being able to identify your sound card.
When this little program has finished, leave the console open and try one of the sound programs, eg, play a cd or an mp3.  If no sound, go back to the console and type
alsamixer (or it may be alsamix), this will start another little program which will tell you if your main output has been muted, or is very low.  Unmute it if necessary, and move volume to about 70% (this can be changed later but the immediate concern is to get sound working).
Test a sound producing program again.  If you have sound, go back to the console and type 
alsactl store
this will save the sound card configuration for you.

If you still have no sound, then there is something else going on, maybe an irq needed by the sound card is being disabled during the boot sequence.  (check the boot messages before Ubuntu starts).  This is rare, but it happened to me on an old Acer P111

---

### Post by yeateg on 2006-06-20
My apologies, I ran the first lot of updates last night, and lost sound.  For some reason alsaconf does not seem to be in Dapper Drake.  So I am now in the same position you are.  When I get sound working again I'll post the solution

---

### Post by yenruoj on 2006-06-21
I think I've found a solution -- EasyUbuntu.  I followed the instructions and everything appears to be working! :-)

---

### Post by bobpaul on 2006-07-04
[QUOTE=yenruoj]I think I've found a solution -- EasyUbuntu.  I followed the instructions and everything appears to be working! :-)[/QUOTE]

I'm still stuck. Tried EasyUbuntu (looks like a less capable automatix) but it didn't help. I'm not having codec issues, my device just isn't recognized in gnome after upgrading from Dapper.

```
# lspci | grep -i audio 
0000:00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
```

```
sudo /etc/init.d/alsa-utils restart
 * Shutting down ALSA...  * warning: 'alsactl store' failed with error message 'alsactl: save_state:1163: No soundcards found...'...        [fail]
 * Setting up ALSA...  * warning: 'alsactl restore' failed with error message 'alsactl: load_state:1236: No soundcards found...'...         [ ok ]
```

There's no alsaconf in dapper that I've found and I can't recal where the text config files are, so I'm stumped.

---

