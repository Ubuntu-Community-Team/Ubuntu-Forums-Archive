---
title: "Skype, Bluetooth and Intrepid"
date: 2008-11-02
forum: Multimedia Software
---

### Post by Halow on 2008-11-02
I have to say I'm quite happy that Bluetooth in Intrepid has a discovery mode. I got a Bluetooth dongle just days before release, hoping I'd get a feel for it first. Under Hardy, that didn't go so well. In Intrepid, things paired quite nicely. Now, with a little work, I've gotten Skype and my Bluetooth headset to work together - for only the *first* call. All subsequent calls give the wonderful "Problem with Audio playback" error, regardless of whether I continue to use the headset or set it back to my mini-jack headset in the audio options of Skype. In order to use the Bluetooth headset for another call I have to un-pair and re-pair, then restart the entire system.

There has to be an easier way! I've tried exiting and re-entering Skype, doing **$ sudo /etc/init.d/bluetooth restart**, restarting only the session. I'm really not sure which service is to blame for this misbehavior (bluetooth or Skype... could even be PulseAudio for all I know). Any help narrowing it down would be wonderful (so at least I can hunt down the bug and submit/report it affecting me).

---

### Post by Halow on 2008-11-03
After some more putzing around with it, I've noticed that it's creating multiple instances of EsounD client in PulseAudio Manager (Clients tab). I'm getting the impression that the headset is continuing to communicate with Skype (and PA) even after the call is finished. I'm no wiz at debugging, but would love to give more info if it would help (and I knew how).

I am truly stumped.:confused:

---

### Post by peyu on 2008-11-06
Hi Hallow,

Using Intrepid, I'm trying to get working a logitech bluetooth headset, I can get it recognized and paired with the bluetooth tool that appears in the notify bar, but then I don't know what to do next... I chose in Skype Options the headset sound device, but it doesn't work...

I suppose I'm missing something, can you explain in details how you get it working ?

Thanks.

---

### Post by Halow on 2008-11-06
I keep toying with it....

Unpairing and repairing the headset, restarting Skype, restarting the bluetooth service and restarting the computer in different orders. Sometimes I get Audio Playback errors, sometimes just loads of static to the other Skype user, and sometimes it actually works. The problem is, I'm starting to get the idea that this is more Bluetooth/Skype's fault than anything else.

My dongle comes up as (in lsusb):  Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
My headset is a Plantronics Explorer 220.
Skype version 2.0.0.72 (from the medibuntu repos).

---

### Post by remu on 2008-11-07
I believe I am having the same problem. I can see my headset through the wizard, and it says it configured it correctly, but then after that I do npt know what to do. I tried to click the connect button, but nothing happens. Any help would be greatly appreciated!

---

### Post by Halow on 2008-11-08
Are you using the headset for Skype? You should have the option in Skype to set it to "headset" in the Sound Options where you have Sound Out and Sound In.

---

### Post by Halow on 2008-11-10
UPDATE!:

I compiled (with only a minimum of hair pulling) the latest version of Bluez from their [site]("http://www.bluez.org/"), version 4.18. Now, running the following after each call will make it so that I can answer the next one on my headset:

```
$ sudo /etc/init.d/bluetooth restart
```

Not a total fix, but a vast improvement (for me). Let me know if this helps (or doesn't) for anybody else.

---

### Post by zoly on 2008-11-11
Hi Halow! I think something is not OK with PulseAudio and Skype. (As Skype is an ALSA-program) Somewhere on the web there is a kind of solution, may be on PulseAudio wiki-site, I don't remember... anyway: I've done everything according to the instruction there, using 8.04, but it did not work for me, don't know why... Now, I'm starting the same way with 8.10, if I'll find the website again :-) I've just starting, I'll report what happened, later.

---

### Post by markbuntu on 2008-11-11
The thread for getting skype to work with pulseaudio in Hardy is here:

[http://ubuntuforums.org/showthread.php?t=937323](http://ubuntuforums.org/showthread.php?t=937323)

Since nobody will tell me if this works with Intrepid or what changes may be needed. I am unable to update it. (I have not had any success getting Intrepid to boot on my machine so I am unable to test this myself.) Your help would be appreciated.

---

### Post by Halow on 2008-11-11
That's the thing. Skype worked just fine by default in Intrepid (with PA too) - with my wired, mic/headphone headset. There seems to be some miscommunication going on either with Bluez or Skype in which it doesn't stop communicating with the Bluetooth headset.

On some of my failed calls routed through the Bluetooth headset Skype will not exit until I've restarted Bluetooth service.

---

### Post by alexeix on 2008-11-13
This is really disappointing.

After not being able to use my Bluetooth headset with Hardy and Skype, I thought the issues may have been resolved in 8.10.

I no longer get errors when pairing (as I did in Hardy), but I get no audio from the headset.

Have tried all the Skype settings...

Are there any other VOIP applications which are recommended?
Something which does PC to PHONE?

Thanks.

---

### Post by kubug on 2008-11-14
How do you guys pair your headset? As soon as I try it, it tries to send a random passkey to my headset, which obviously is wrong, and it just fails to connect. 

I had to install Blueman to get things working for me.

---

### Post by alexeix on 2008-11-14
I get the same scenario - passkey sent to headset message.  No error occurred, so I presumed Ubuntu worked out that it was a headset (therefore with no way to enter a passcode).

So with Blueman, does it work correctly, consistently?

---

### Post by kubug on 2008-11-14
> **alexeix said:**
> I get the same scenario - passkey sent to headset message.  No error occurred, so I presumed Ubuntu worked out that it was a headset (therefore with no way to enter a passcode).

So with Blueman, does it work correctly, consistently?

It seems to work better for me. Now, it's not as integrated as the other bluetooth manager, but it works for me.

---

### Post by alexeix on 2008-11-16
Where did you install Blueman from?

I can't find a version for Intrepid.

---

### Post by kubug on 2008-11-16
> **alexeix said:**
> Where did you install Blueman from?

I can't find a version for Intrepid.

I can't find the place I got it from, somewhere on launchpad, but here is the repository:

deb [http://ppa.launchpad.net/blueman/ubuntu](http://ppa.launchpad.net/blueman/ubuntu) intrepid main

Please note the last two posts on this thread BEFORE installing: 

[https://bugs.launchpad.net/blueman/+bug/283141]("https://bugs.launchpad.net/blueman/+bug/283141")

---

### Post by mgol on 2008-11-26
It's weird for me that You only have problems with Bluetooth. I use standard headphones and Skype installed from medibuntu repo doesn't work. I cannot send any sound, I don't hear a person I'm talking to. I only hear Skype sounds (when sb calls etc.).

Is there anything I should try?

---

### Post by psyke83 on 2008-11-26
> **mgol said:**
> It's weird for me that You only have problems with Bluetooth. I use standard headphones and Skype installed from medibuntu repo doesn't work. I cannot send any sound, I don't hear a person I'm talking to. I only hear Skype sounds (when sb calls etc.).

Is there anything I should try?

What you need to do is a) configure PulseAudio properly, b) configure PulseAudio's default playback and recording devices, and c) configure Skype to use PulseAudio correctly.

See: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by peyu on 2008-11-27
In my case, Skype works successfully with my bluetooth headset. I installed blueman because it's easier(but it works also with the bluetooth gnome applet).

1) Pairing headset
2) Adding to .asoundrc these lines:

```
pcm.headset {
    type bluetooth
    }
```

3) Restart, to take into account the new .asoundrc
4) Pairing with blueman the headset
5) Activate audio service
6) Select "headset" in skype input and output.

But I've got a problem using the headset with pulseaudio...

When I type 
```
aplay -D headset -f s16_le /usr/share/sounds/question.wav 
```

It works, but the sound plays very slowly and I get this output:
```
Playing WAVE '/usr/share/sounds/question.wav' : Signed 16 bit Little Endian, Taux 44100 Hz, Mono
Attention : incorrect rate (asked = 44100Hz, obtained = 8000Hz)
         Please use plugin (-Dplug:headset)
```

And with pulseaudio it's almost the same, the sound is very creapy.

So does anybody know how to indicate to alsa, bluez or pulseaudio that the max rate of my headset is 8000Hz ?

Thanks a lot if you have any idea !

---

### Post by macabro22 on 2008-11-30
Do you guys also only get audio on left side?

---

### Post by Halow on 2008-11-30
Skype only seems to offer up mono, and it wasn't until I had Pulseaudio in place that I would get said mono stream from both sides. That is with my standard, old style, two plug headset.

I have still not perfected the Bluetooth and Skype thing, as the new Bluetooth headset I bought simply gave up the struggle and my old one is rather uncomfortable.

---

### Post by sicofante on 2008-12-01
> **macabro22 said:**
> Do you guys also only get audio on left side?
Yes, that happens here. I got audio on both sides at some point while struggling with it the whole weekend, but I'm back again to left channel only.

I don't know if it's the poor PulseAudio implementation in Ubuntu or the weird way of naming things on the Skype client, but this is a royal mesh and I just gave up.

And it's not only the naming on both sides, which no ordinary human being would understand; it's the Bluetooth implementation too. The default BT manager in Ubuntu is so simplistic it's useless at troubleshooting. Blueman doesn't help either: When I use it my headset keeps staying in a loop of connect/disconnect. The headset works flawlessly with any phone, of course.

I hope this is addressed soon in Ubuntu because it's a deal breaker for some of my customers.

:-(

---

### Post by Trek1701 on 2008-12-05
I'm having a similar problem with my headset. It keeps connecting and disconnecting all the time.
Any ideas about what could be it? Anything I can do to help solving this?
Thanks,
Trek1701

---

### Post by jhagmar on 2008-12-24
Any answers to this problem yet? I have the exact same problem as described in the first post. Using the headset works beautifully for the first call in Skype, using the "headset" device for sound input and output. After that, I have to restart the bluetooth daemon to avoid the "Problem with Audio Playback" error. In fact, this works best if I stop the daemon, wait a few seconds and then start the daemon, instead of restarting immediately.

/Jonas

---

### Post by fooblah on 2008-12-27
Seems to work fine for me using blueman ppa (which includes several updates for bluez and other packages).  I am able to make multiple calls.  

I also added the lines mentioned above to my .asoundrc (it actually didn't work at all until I did that).

In skype audio options I have set sound in/out to headset and ringing to pulse.

I have noticed that on my headset there is an extra beep when the audio stops that I think means things have properly disconnected.  With skype there are lots of pauses and then extra sounds like the hangup sound where it will connect and disconnect a few times.  I am always very careful to not try and make another call until I've heard that last disconnect beep so maybe that is keeping me out of trouble.  I also think this might be helped by turning off all those little sounds, especially the disconnect sound in skype settings.

The ppa I'm using to install blueman and bluez updates is:

deb [http://ppa.launchpad.net/blueman/ubuntu](http://ppa.launchpad.net/blueman/ubuntu) intrepid main

I haven't tried using my call control button to answer or disconnect either so maybe that is another reason I'm staying out of trouble.  I also would be shocked if that level of integration existed between skype and my headset so I'm almost positive it wouldn't work anyway.

---

### Post by Halow on 2008-12-27
Ah... I had been compiling bluez from their site. Perhaps I should give the ppa a go. Thanks.

Also, the call button works in Vista. Never worked for me in Ubuntu.

Bluetooth is an on-again-off-again problem for me. One would think by now I'd have things settled, but I'm no pro.

---

### Post by igorgomes on 2009-01-24
Hello all,

Please check my solution: https://bugs.launchpad.net/ubuntu/+source/linux/+bug/268502/comments/50

It worked and now I can successfully pair (and talk of course) my bluetooth headset (Plantronics 510).

Cheers,

Igor Gomes

---

### Post by doudar on 2009-03-11
I've finally got this working with my plantronics 520 on intrepid with skype. 
 
After adding the .asoundrc file and the blueman ppa, the headset was working but I was still unable to make multiple calls in skype without restarting bluetooth closing skype and repairing the headset.  
 
What worked for me was disabling all of the extra sounds in the skype options menu and now I'm able to make successive multiple calls! 
 
Enjoy!

---

### Post by doudar on 2009-03-11
Okay, after a day of testing the above works, but only for about 3 hours. Then I have to re-pair the headset, restart skype and bluetooth.

---

### Post by mtron on 2009-10-06
just wanted to throw in my experience on that subject. Pairing was very easy on intrepid via the bluetooth applet but step after step:

- **install** libasound2-plugins and bluez-alsa packages from the repositories 
```
sudo apt-get install libasound2-plugins bluez-alsa
```

- **edit**/populate **~/.asoundrc** with:

```
pcm.bluetooth {
  type bluetooth
  device 7B:16:21:33:F2:7G
  profile "voice"
}
```

Replace the 7B:16:21:33:F2:7G with the mac of your bluetooth headset. hcitool scan will tell you yours.

- **pair** the device via the gnome-bluetooth applet (pin is in my case "0000", refer to your headsets manual if this one doesn't work for you)

just fo be sure: after the pairing completed, use "hcitool con" from a terminal. This will display all active connections so it should display your headset's mac address:

> Connections:
	< ACL 7B:16:21:33:F2:7G handle 42 state 1 lm MASTER 

- **test** it with mplayer 
```
mplayer -ao alsa:device=bluetooth /path/to/audio.mp3
```

after some seconds mplayer should start playing. If you get an error from mplayer like 

> [AO_ALSA] alsa-lib: pcm_bluetooth.c:1531:(audioservice_recv) Error receiving data from audio service: Success(0)
[AO_ALSA] alsa-lib: pcm_bluetooth.c:1547:(audioservice_expect) Bogus message BT_SETCONFIGURATION_REQ received while BT_SETCONFIGURATION_RSP was expected
[AO_ALSA] Unable to set hw-parameters: Invalid argument restart the bluetooth subsystem

check that you have successfully paired the headset (with "hcitool con" see above), and restart the bluetooth subsystem with: 

```
sudo /etc/init.d/bluetooth restart
```

after that mplayer started playing (ot of magic for me :) ) and it also came out of my headset.

- **skype**: in skype go to "Options - sound devices" and choose "bluetooth" for sound-in and sound-out. i kept the default device for ringing, so incoming calls ring via the Computer speakers.

To avoid the "locked" bluetooth headset after a call has ended, just disable all the extra sound files in the Notifications tab of the skype settings. i disabled the sound notification for Number busy, call failed, call missed, call hungup and call ended.

If skype locks the device anyway, just restart the bluetooth subsystem (see aboce for the command) You don't need to restart skype nor re-pair your device in that case.

- **wake-up**: my headset goes in a hibernation state after it's not used for 10 minutes. So to reconnect it i need to bring it in pairing mode (a 3 sec push on the power button in my case) and while it's in pairing mode, click the small "Connect" button for the device (you can get there by right-clicking on the bluetooth panel icon and choosing Preferences). After that, the headset can be used again. 

So that's it. Thanks to everyone in this thread i have a nice working BT headset in intrepid now :)

---

