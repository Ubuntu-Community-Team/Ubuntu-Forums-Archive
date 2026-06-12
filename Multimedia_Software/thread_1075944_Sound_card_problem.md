---
title: "Sound card problem"
date: 2009-02-20
forum: Multimedia Software
---

### Post by NastyTribe on 2009-02-20
Hello there...

It's my first thread in this forum...
I'm new at linux world. I've always been a windows (xp and vista) user. Now, for the first time I'm trying out linux (Ubuntu 8.10).
I've already installed it and now I'm facing my first problem. My sound card (Soundmax) is not working (driver problem), despite all my attempts to make it work.
I do not know how to use the command line, so I really need help.

Best regards.

---

### Post by forestwalkerjoe on 2009-02-20
this maybe very simple .. in a way.. here is one very good way to get your systems sounds back on. Try it.. if it fails.. find my name on the left here and write me an instant message. BUT only please.. IF you try [this solve]("http://ubuntuforums.org/showthread.php?t=789578").
This works on many systems. 

good luck. 
FWJ

---

### Post by vginov on 2009-02-20
Hi
[B]
:WELCOME TO THE WORLD OF OPENSOURCE:[/B]

Can you write what kind of error message you are getting?

Because most of the time the codecs for sound is not installed you have to install it. 

If you are not able to play your audio files then 

type the bellow command

sudo apt-get -y install gstreamer*

and give your password 

and if you want most of the DVD and VCD players then follow the bellow steps 

go to Applications > Add / Remove .. in the search box type DVD Player 

And check all the applications you get there and Apply Changes 

Once all the files are being installed then you will be ok with the sound problem 

Never hesitate to ask we are always here to guide you to get the best ....

---

### Post by NastyTribe on 2009-02-20
Hello again...

I tried to solve the problem with the solutions of vginov and forestwalkerjoe, but it didn't worked.
The problem is with de driver: ubuntu does not "recognize" my sound card.
Whe I click on the sound icon in the tray a error messenge appears: Did not found any plugin and/or GStreamer volume control device.

---

### Post by Yellow Pasque on 2009-02-21
Please post output of:
```
lspci
```
If your sound card is very modern, you may have to install ALSA from source using this script - [http://ubuntuforums.org/showthread.php?p=6589810](http://ubuntuforums.org/showthread.php?p=6589810)

---

### Post by NastyTribe on 2009-02-21
Hi...

After typing "lspci":

00:00.0 Host bridge: Intel Corporation 440FX - 82441FX PMC [Natoma] (rev 02)
00:01.0 ISA bridge: Intel Corporation 82371SB PIIX3 ISA [Natoma/Triton II]
00:01.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:02.0 VGA compatible controller: InnoTek Systemberatung GmbH VirtualBox Graphics Adapter
00:03.0 Ethernet controller: Advanced Micro Devices [AMD] 79c970 [PCnet32 LANCE] (rev 40)
00:04.0 System peripheral: InnoTek Systemberatung GmbH VirtualBox Guest Service
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 08)


--------------------------------------------------------------------------

Now I will try to install ALSA, as you recomended.
Thank you for trying to help me!! :)

Best regards.

---

### Post by NastyTribe on 2009-02-21
Still with no solution to my problem...
If anybody could help, I'll be very thankful.

---

### Post by markbuntu on 2009-02-21
Are you running in virtualbox?
It looks like you are.
If so you need to enable sound services for virtualbox guests so Ubuntu can find the sound hardware.

---

