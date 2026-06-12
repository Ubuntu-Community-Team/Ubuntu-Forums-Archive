---
title: "no sound with ´CM6501 Audio Codec´ - Card"
date: 2008-04-06
forum: Multimedia &amp; Video
---

### Post by jochne on 2008-04-06
Hi guys,

after upgrade from 7.04 to 7.10, I got a problem with my sound: there is none.

I have checked a few things and postet the results here:

[http://ubuntuusers.de/paste/159315/](http://ubuntuusers.de/paste/159315/)


Thank you for any help, i am quiet new at Ubuntu and almost desperate,
jochne

---

### Post by Metaljaz on 2008-04-07
Right click on the volume control icon on the top right hand screen. Select preferences and check which device you are controlling. Then try using PCM as the track.

---

### Post by jochne on 2008-04-08
Hi Metaljaz,

thanks for the reply. Under   Volume Control -> Preferences   theres only one device selectable: 'USB Mixer (OSS Mixer)'
I have the choice between three tracks: 'PCM', 'Microphone', 'PCM-2'
and tried them all: nothing worked :(

Greets, jochne

p.s.: i forgot to say what else i did:

1) System -> Preferences -> Sound     all Buttons to 'USB Audio'

          =>   still no sounds at all

2) 'asoundconf set-default-card default'  in terminal

both things seem to work for many users, but here: nothing

---

### Post by Metaljaz on 2008-04-08
Did you try this thread? If not, read all the post.

[http://ubuntuforums.org/showthread.php?t=379429](http://ubuntuforums.org/showthread.php?t=379429)

---

### Post by jochne on 2008-04-09
Hi Metaljaz,

i went through all the things mentioned in the thread (except from installing ossv4 for it doesn't seem to support the cm6501-chipset)

in detail:

1.) in   '/etc/modprobe.d/alsa-base'
   the line   'options snd-usb-audio index=2'
   must be changed to   'options snd-usb-audio index=0'
   (or simply deleted or commented out, as i found out)
   to make ubuntu set my card to   'card 0'

2.) in terminal   'asoundconf set-default-card default'   because  'default'
is the only card appearing in  '/proc/asound/cards'

3.) set all buttons in   'System -> Preferences -> Sound'
   to  'USB Audio'
   many guys mentioned that this helped them, in my case, nothing
   happened. I can use the  'Test'-buttons, it goes  'Testing ...'  but not a beep.

4.) i removed   'linux-sound-base', 'alsa-base', 'alsa-utils'   and reinstalled
   them
   (after that, i had to repeat step 1)

5.) i added the following lines to   '~/.asoundrc'
   'pcm.usb-audio {
    type hw
    card 0
    }
    ctl.usb-audio {
    type hw
    card 0
    }'

6.) checked that the selected track is 'PCM'


but still no sucess. I am getting confused here:
- apparently my soundcard is detected, and the usb-audio-driver is there
- I dont get any error messages, i can start e.g. totem, vlc... they do work - 
  except that i can't hear any sound at all :(

If i hadn't my ManoWar-loving neighbour, i'd start to believe i'm deaf ;)

---

### Post by Metaljaz on 2008-04-09
> **Metaljaz said:**
> Did you try this thread? If not, read all the post.

[http://ubuntuforums.org/showthread.php?t=379429](http://ubuntuforums.org/showthread.php?t=379429)


I don't have the CM6501 card but thought I would try and help you out. I read through the above post and really thought it would help you solve your problem. Don't give up just yet, especially with Ubuntu. 
If you did an update thru synaptic you may try a fresh install of 7.10. The new release will be out, in a matter of days, and the issue maybe resolved.

---

### Post by jochne on 2008-04-09
Hi Metaljaz,

thanks for your help, posting that thread was a good idea; searching the forum and "googling" shows that the solutions there did it for almost all.

Bad thing to say: no progress here.

Meanwhile i tried:  I updated   ALSA  from  1.0.14  to  1.0.16.  Curious about that:   'alsaconf'  does NOT recognize my card at all  :confused::confused::confused:

[quote=Metaljaz]Don't give up just yet, especially with Ubuntu. [/quote]Don't worry, i never give up :)



Greets, jochne

---

### Post by Metaljaz on 2008-04-09
Much as I have been reading about this card you would think I have one.....but I learn a lot while trying to help.

These links may or may not help but they explain what maybe going on with your sound. Its  different versions of linux but similar issue.

[http://www.linuxquestions.org/questions/linux-software-2/alsa-problems-on-my-pc...-543114/?highlight=CM6501+Audio+Card#post2696503](http://www.linuxquestions.org/questions/linux-software-2/alsa-problems-on-my-pc...-543114/?highlight=CM6501+Audio+Card#post2696503)

[http://www.linuxquestions.org/questions/debian-26/48000hz-bitrate-audio-distorted-508691/?highlight=CM6501+Audio+Card](http://www.linuxquestions.org/questions/debian-26/48000hz-bitrate-audio-distorted-508691/?highlight=CM6501+Audio+Card)

---

### Post by jochne on 2008-04-10
Whew, that was a lot of homework, thanks for the interesting links.


> **Metaljaz][http://www.linuxquestions.org/questi...rd#post2696503]("http://www.linuxquestions.org/questions/linux-software-2/alsa-problems-on-my-pc...-543114/?highlight=CM6501+Audio+Card#post2696503")[/quote]
I have read through all that. But if I got it right, these guys are trying to install a mixer (dmix, jack) so that one can use more than one application at the same time.
I don't wont to take step2 before i took step1 said:**
> [http://www.linuxquestions.org/questi...501+Audio+Card]("http://www.linuxquestions.org/questions/debian-26/48000hz-bitrate-audio-distorted-508691/?highlight=CM6501+Audio+Card")
the problem here is quiet obviously an older version of the alsa-driver and should be solved in the new version. And, again, the guy there CAN hear sound, though in bad quality. My boxes are completely quiet.


Meanwhile I checked that my boxes were ON, and that they are plugged in correctly. I am running out of ideas here...:-k

---

### Post by jochne on 2008-04-11
Hi guys, hi Metaljaz,

here is just an update. I found the time to completely reinstall 7.10 today, but situation hasn't changed at all. So i went through the steps i mentioned before again.

Doing this, two things came to mind:

1.) don't know why, but i couldn't get my sound to work under my 7.04 LiveCD. That's strange, i'm sure i had sound before i upgraded to 7.10.
Is it even possible that my 7.10 installation could influence a 7.04 LiveCD :confused:

2.) running vlc under my brand new 7.10, i get an error message (this hasn't happen before). It reads:

'[00000337] main audio output error: no decoder thread'

Maybe someone can do something with that, i can't make anything out of the results google delivers.


Thanks for any idea,
greets,
jochne

---

### Post by deadgobby on 2008-04-11
Please open up the terminal and input this command and please post back the reply
aplay --list-devices 

Gobby

---

### Post by jochne on 2008-04-11
Hi Gobby,

$ aplay --list-devices 
**** List of PLAYBACK Hardware Devices ****
card 0: default [PnP Audio Device        ], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

---

### Post by deadgobby on 2008-04-12
Ahhhh it see two devices. So you can do this. Double click on the sound icon. Go to File>Change Devices and select your USB one. THe other route is to try going into BIOS and disable the on board sound device.

---

### Post by jochne on 2008-04-12
Hi Gobby,
thanks for your help.


1.) I disabled my on board sound card in bios. As an result it is no longer recognized:

'$ aplay --list-devices 
aplay: device_list:207: no soundcards found...'

that didn't surprise me too much for i only have the on board sound device ;)
I enabled it again.
 

2.) You are right, under   'Sound icon -> Open Volume Control -> File -> Change devices'   i can select two devices, as i can under  'Sound icon -> Preferences'  and  'System -> Preferences -> Sound -> Device'

This two devices would be
a) 'PnP Audio Device (Alsa Mixer)'
b) 'USB Mixer (OSS Mixer)'

Could this be because of the lines i added to the  '~/.asoundrc' - file?  (See post #5, 5.) )

I am a little bit confused here because i only have one sound card. Anyway, i tried both devices, nothing works.


3.) After that, i played a little bit around in the VLC player. Under  'Settings -> Preferences -> Audio -> Output modules'  i have some choices. I tried  'default' first, that gave me the

'[00000337] main audio output error: no decoder thread' - error message.

Then i took  'ALSA audio output'  and  under  'ALSA'  i used the  'Refresh list' - button. That gave me the choice between  'Default'  and  'PnP Audio Device: USB Audio (hw:0,0)' .  Both resulted in the error message above.


Thanks for listening, any idea is welcome of cause,
greets, jochne

---

### Post by deadgobby on 2008-04-13
Does your sound mixer looks like this? Make sure all so under that the under the switches tab that the iec958 is check off.

---

### Post by jochne on 2008-04-13
Hi Gobby,

sorry i'm not sure if i understood you. So i took two screenshots of my sound mixer to show you:

---

### Post by deadgobby on 2008-04-13
Ummm. No!
 Go into Edit>Options and see if you can get the options I taken a screen shot of. 
Mainly it is going to Analog Front that is going to get the sound going through. If that does not work. Gripes USB can be a pain in the***** Please fill in the blank of the body part**** 
Gobby

---

### Post by deadgobby on 2008-04-13
Oh poop on the stick. I forgot the screen shot.

---

### Post by deadgobby on 2008-04-13
I thought of some thing. Have you installed firmware? I wounder if it requires firmware?

---

### Post by jochne on 2008-04-13
Hi Gobby,

[quote=Deadgobby]Ummm. No!
 Go into Edit>Options and see if you can get the options I taken a screen shot of.[/quote]
Sorry, but i'm still not sure what you mean. I opened  'Edit -> Preferencees'  (there's no  'Options'  here) and provided the screenshot. It's the lower one in my attachment. Here you can see all the options i can choose. Please be a little bit more specific, i really appreciate your help, but i couldn't figure out what exactly you wanted me to do.


[quote=Deadgobby]I wounder if it requires firmware?[/quote]
Interesting point. Searching the web i couldn't figure out, but ASRock doesn't seem to offer any firmware to the board at all, and for the CM6501 - chipset: nothing else but a few drivers for Windows. I found that at ALSA-project:

[http://www.qbik.ch/usb/devices/showdev.php?id=3925](http://www.qbik.ch/usb/devices/showdev.php?id=3925)

They claim the CM6501 is fully supported by the generic USB-Audio-Driver.


greets, jochne

---

### Post by deadgobby on 2008-04-19
try this link and read up and see if can help you.
[https://wiki.ubuntu.com/EasyUsbAdsl?highlight=%28usb%29](https://wiki.ubuntu.com/EasyUsbAdsl?highlight=%28usb%29)
Gobby

---

### Post by jochne on 2008-04-19
Hi Gobby,

[quote=Deadgobby][https://wiki.ubuntu.com/EasyUsbAdsl?highlight=%28usb%29](https://wiki.ubuntu.com/EasyUsbAdsl?highlight=%28usb%29)[/quote]

I went through all that but couldn't find out much useful there. It all deals with the firmware of some special modems. But it brought to mind that some usb devices can be really difficult to handle under Ubuntu.

So i started a search for firmware again but didn't find any. The only things offered are some Windows drivers and an BIOS update for the mobo.


Meanwhile i noticed that  'lshw'  doesn't seem to list my usb-card. But it's found by  'aplay'  etc.  :confused:

btw: I added a few plugins to the VLC, as osd, esd, and tested them; all resulting in the 'main audio output error: no decoder thread' - error message.


greets, jochne

---

