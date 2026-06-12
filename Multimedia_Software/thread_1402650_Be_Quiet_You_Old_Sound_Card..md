---
title: "Be Quiet You Old Sound Card."
date: 2010-02-09
forum: Multimedia Software
---

### Post by mdrake36 on 2010-02-09
Ok so all my Sound Utilities work and I have my audio priorities straight I think.
I uninstalled Pulse Audio and Now can lock down memory.
AWesome.
BUT..... somewhere in the process my sound card got kinda Whiny. you know like a high pitched modem sound coming through.
I can silence the sound by Starting an application like Ardour then Terminating the Jack Engine. After Terminating the Jack Engine the Sound card is as quiet as a mouse. I can even restart the Jack Engine and the Card stays quiet. Its only when I close the Offline Adour program that the Whine comes back. Also If I were to restart the Jack connection within the Ardour session it would come back. Otherwise if I were to leave Ardour Idle in the background disconnected from the Jack Engine the Card is perfect. 
This is very embarrassing when Comparing qualities with say a Mac Book Pro.

Compaq R3000 (I know don't say it)
ATIIXP sound Card



                                                                                                   [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]                            [[IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]]("http://ubuntuforums.org/report.php?p=8799607")                                                                       [IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG]             [[IMG]http://ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://ubuntuforums.org/editpost.php?do=editpost&p=8799607")                                        [[IMG]http://ubuntuforums.org/images/buttons/quote.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=8799607")                               [[IMG]http://ubuntuforums.org/images/buttons/multiquote_off.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=8799607")                               [[IMG]http://ubuntuforums.org/images/buttons/quickreply.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=8799607")                                                                                                                   mdrake36                   [View Public Profile]("http://ubuntuforums.org/member.php?u=983352")                   [Send a private message to mdrake36]("http://ubuntuforums.org/private.php?do=newpm&u=983352")                             [Find More Posts by mdrake36]("http://ubuntuforums.org/search.php?do=finduser&u=983352")               [Add mdrake36 to Your Contacts]("http://ubuntuforums.org/profile.php?do=addlist&userlist=buddy&u=983352")                
                                                                                                                          [CENTER]         [New Reply       ]("http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=8799607")[/CENTER]

---

### Post by cariboo on 2010-02-10
A bump for the move.

---

### Post by mdrake36 on 2010-02-22
I though that it was tied to the fact I had uninstalled pulse. But no Dice even with pulse installed the card is noisy. For now I boot Ardour and then terminate then re-start Jack engine without restarting Ardour. The answer seems right there in front of me.
 
 
BUMP

---

### Post by cchhrriiss121212 on 2010-02-23
So does this sound come from the hardware or out the speakers?
And the ATIIXP is an internal sound device on your laptop? You might want to consider an external sound card for better performance when making music.

---

### Post by mdrake36 on 2010-02-25
The actual device is making the noise and it is audible through the speakers faintly.
What is strange is by opening Ardour and resetting the Jack engine and leaving the Ardour connection disconnected smooths the cards temper. Its as if Ardour occupies a request from the sound card. 
Without out Ardour other applications try unsuccessfully to quiet the card but ultimately only interfere with the Card noise. The application seem to work correctly, ALBEIT NOISY.
Might this issue be a result of the interrupt priorities. Ardour is doing something correctly I just can't nail down exactly what it is.

---

### Post by mdrake36 on 2010-03-01
Wow I didn't know this would be such a puzzle. I did some research and came across an article that made a light bulb go off. I don't think my sound card is an ATIIXP sound Card.:idea:
Which explain the Problem. Infact my sound card doesn't have a name only a Number (poor Robot) [B]435664320011.
Any way I could try differnt drivers?

Bump
[/B]

---

### Post by Yellow Pasque on 2010-03-01
What you are describing sounds like coil whine. It can get worse over time.
> I don't think my sound card is an ATIIXP sound Card
If you have an integrated ATI chipset, then the sound card will be listed as an ATI, even if it's a generic AC97 or HDA codec. The surest way to find out what device you have and what driver is in use:
```
lspci -vv
```

> Any way I could try different drivers?
The correct driver should be pre-installed/loaded, but you can try upgrading to the latest ALSA: [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

---

### Post by mdrake36 on 2010-04-09
> **Temüjin said:**
> 
The correct driver should be pre-installed/loaded, but you can try upgrading to the latest ALSA: [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

Thanks You were right!
correct driver. but I am now leaning towards the realtime capabilities of my Distro "Studio"
When I run Kubuntu or Xbuntu non-realtime kernel the card is quiet as a mouse.
somewhere in the realtime priorities the card gets tempermental. :guitar:
I should probably invest in a real sound engine like a Firepod or something?

by the way "My disk did died right now" I am running with no hard drive at all right now storing all my crucial data on my grey matter.

Update No its the Jack server for some reason my sound card just won't play nice with Jack probably just old and worn out.

---

