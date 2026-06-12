---
title: "stop microphone feedback?"
date: 2006-07-31
forum: Multimedia &amp; Video
---

### Post by bullgr on 2006-07-31
hi...

i have a simple headset who plugs to the line-out and microphone jack of my sounblaster audio card.

my question is how can i stop the microphone feedback to the headset and the speakers?

i tryed also the headset in winblows too. an i figure out that the microphone is not returning the sound to the headset or to the speakers. its silendly dead but works great.

thanks...

---

### Post by x64Jimbo on 2006-07-31
You could turn the microphone off when you're not using it. Most microphone headsets have a mute button/slider. Or you could use the mixer in Ubuntu to turn it off in the software.

---

### Post by adamkane on 2006-07-31
The fact is your earphones are picking up the sound from your mic and speakers. The only way to eliminate this is to use earphones that cover your ears well, and do not pick up outside noise. Also your headset may have a gain setting you can adjust.

---

### Post by bullgr on 2006-07-31
my problem is not how i mute the microphone, my problem is when i use it the sound that capture the microphone returns to the headset and to the speakers.
i hear that i say in the microphone.

in winblows this is not happen. the microphone works great and no sound is returning to the headset and to the speakers.

i also try to combine all the posible setings i could in alsa mixer but the problem remains.

---

### Post by x64Jimbo on 2006-07-31
Oh sorry when you said feedback I thought you meant that loud screeching sound that comes from not muting the mic. Hehe. 
See if this works for you:
[http://ubuntu.wordpress.com/2005/12/05/fixing-the-errant-microphone/](http://ubuntu.wordpress.com/2005/12/05/fixing-the-errant-microphone/)

---

### Post by bullgr on 2006-07-31
adamkane you was faster than me... :KS 

ok, lets say the headset are cause the problem...
why is this not happen in winblows?
in winblows the microphone is silendly dead, no return sound to the headset and to the speakers, but works great. then i speak in the microphone i dont hear that i say...

---

### Post by adamkane on 2006-07-31
I had it wrong. I think your mic is picking up the sound from your speakers.

My only answer is that your audio program is turned off in Windows.

Turn off your speakers while using your headphones.

---

### Post by bullgr on 2006-07-31
thanks x64jimbo and adamkane for the quick response...

ok, after your sugestions i see that when i mute central i just dont hear anything.

now i can use the microphone to record something.

but when i use the headset for Voip (skype)?
then i can't hear nothing :sad:

---

### Post by x64Jimbo on 2006-07-31
Maybe change the input in Skype?

---

### Post by bullgr on 2006-07-31
no guys, i believe it's something more complicated...
the microphone must not return any sound to the headset and to the speakers.  the output must be silend when i speak to the microphone.

and this must happen in any application in our system.
when i boot in ubuntu and i talk in the microphone it must no return sound.
i don't know if this is a linux or alsa wikness.

have this problem another users too? how works your headset?
sould i buy a usb headset or is there the same problem?

---

### Post by mpvano on 2006-08-01
man amixer

If you figure out exactly which settings need to be different between the skype program and everything else, then you can use  amixer commands in a bash script to change just those settings and then launch skype. You can also restore the settings after skype returns to the script.

I often make such scripts, test them from the command line and store them in a local directory called "bin" in my home directory. Once you have made such a script, you can make a custom gnome applet icon to start it instead of using the program's normal menu entry. You can do this with any program that you manually start. (You can do it to programs launched by other programs too, but that's more complicated).

Sorry if this means learning how to use the command line and write simple bash scripts, but it's a useful skill and this kind of scripts can be quite easy to write...

Hope this points you in the right direction...

Mario

---

### Post by vampyrebytes on 2006-11-26
I believe he is referring to playthrough.

In windows, you can (and indeed must) separately control output and input volumes (including muting). When in windows, the mic can be muted in output and still be able to record.
As far as I have found with all my fiddling around with teh mixer.. this is not true for ALSA. There is only one "mute" and if you mute teh mic, you mute all input, thereby muting all output.

This is bad practice. Even in a headset environment, this can lead to feedback, loopback and echoes.

I have several people that have asked me not to call them on Skype anymore due to the echoes... and yet when I call them via Skype from Windows, they don't even notice. Because I can mute mic output without muting mic input.

I do not want to be able to hear my mic through my speakers or headset at all. But I do want the mic to pick up sound and record it, or send it via Skype, or any other software I happen to be using.

---

### Post by toad60 on 2006-12-23
I have to use Windows for Skype for exacly the same reason!

---

### Post by Spent Casing on 2006-12-23
I just spent 2 days playing with settings to eliminate feedback and echo while using teamspeak.

I don't know exactly what setting eliminated it but, we can try things one step at a time.

Open a terminal and type ```
alsamixer
```

Hit F4, it should open the 'Capture' tab.  Lower 3D Contr, Syth and PCM to 0, and see what that does. If it doesn't work we can try a few others.

---

### Post by PrimoSauce on 2007-01-30
I have the same basic Mic setup (soundcard jacks, not USB) and had the same feedback problem with Skype.  I read this post, played around with alsamixer, and found that muting the mic with capture on made it behave perfectly.  No feedback, no echo, and I could boost it as high as I wanted for pickup.  

If I can help, I can look up the other settings I have for alsa.  BTW, I am running Xubuntu... no gnome goodies or kde.

---

### Post by afritzse on 2007-07-08
This solved my hardware playthrough problem under Ubuntu Feisty Fawn 7.04, as well. Thanks.

---

