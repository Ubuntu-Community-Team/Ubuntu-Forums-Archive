---
title: "Bluetooth Headset and Pulse"
date: 2009-01-19
forum: Multimedia Software
---

### Post by curlybap on 2009-01-19
Hi everyone.  I've had a Google and can't find anything that really helps, hopefully you'll be able to.

I'm running Intrepid on i686, kernel 2.6.27-9.

I got a Bluetooth headset last week and have had trouble setting it up.  It is paired using Blueman and connects then disconnects as it should (I'm told) when I turn it on.

Currently, my .asoundrc file contains the following:
```
pcm.bluetoothraw {
	type bluetooth
	device 00:1A:7D:0D:21:6D
}

pcm.bluetooth {
	type plug
	slave {
		pcm bluetoothraw
	}
}

```

bluetooth is then an option in Skype's Sound Devices options.  When selected a test call appears to work (i.e. no error messages shown), but I cannot hear any sound.

Using ```
pactl load-module module-alsa-sink device=bluetooth
``` I can make the Bluetooth headset show as an output in Pulseaudio Volume Controller's Output Devices tab.

If I then start to play an audio file, it plays through CA0106, my default output.  Clicking the dropdown for it in Playback, followed by 
Move Stream... ALSA PCM on bluetooth (bluetoothraw) via DMA
makes Totem, Rhythmbox or the Sound Preferences window freeze (whichever is playing the sound).

Using ```
pactl load-module module-alsa-source device=bluetooth
``` gives a ```
Connection failure: Connection terminated
``` error, and nothing can connect until I run ```
pulseaudio -k; pulseaudio -D
``` after this.

Can anyone help?  It'd be very helpful if you could, as I specifically bought the headset in the hope it would work with Skype.

Thanks.

---

### Post by John Jason Jordan on 2009-01-23
I have had similar problems, but haven't gotten as far as you.

First, here is a how-to that has helped a lot of people:

[http://ubuntuforums.org/showthread.php?t=1047959&highlight=bluetooth]("http://ubuntuforums.org/showthread.php?t=1047959&highlight=bluetooth")

I tried to post in that forum but I can't register because it won't accept an e-mail address from gmail. 

In my case it hangs on the pactl commands (if pulseaudio is running when I issue the command) and pulseaudio then hangs hard. I have to kill it with kill-9. Strace gives no error messages, nor is there anything in any log files that I can find.

If pulseaudio is not running when I run the pactl command, then I get a connection refused error message.

In my .asoundrc file I have set the device name to drbt50 and that is what I use in the pactl commands. I have rebooted numerous times to make sure the settings in the .asoundrc file are what are being used.

The headphones are beautifully paired in the bluetooth applet. When I turn them on the little power plug icon appears in front of the gold star in the bluetooth preferences window. They also work fine with the bluetooth transmitter that I bought to use with my iPod. 

The headphones worked flawlessly with Hardy. All I had to do was turn them on before launching a sound app. It was after the upgrade to Intrepid that I discovered they no longer worked. And I mean I have never gotten so much as a click or a peep out of them.

I can find pages and pages of posts about problems with bluetooth headphones, but none with a solution that works.

But I'm not going to shut up or quit until I find the solution.

Oh, I should add that I just tried a Jaunty live CD and had exactly the same problem. I spent an hour with the live CD. I got them paired fine, but no way could I get sound out of them.

I need more suggestions.

---

### Post by 005587 on 2009-03-25
did you ever find anything that worked?

---

### Post by John Jason Jordan on 2009-03-25
> **005587 said:**
> did you ever find anything that worked?

No.

After my post on January 23 I tried a few more things, including completely uninstalling Pulseaudio. Nothing has worked.

However, the other day someone posted a message on a bug report that I was subscribed to. The message said everyone should be using Blueman. Blueman is a GUI bluetooth manager. I used to use it a long time ago, but when I upgrade to Intrepid it was no longer complatible. There were some tricks on the Blueman website for getting it to work with Intrepid, but they didn't work for me. Seeing the message on the bug report reminded me of Blueman, so I went to their website and there is now a version for Intrepid, and I have it installed and working. You can get it and instructions here:

[http://blueman-project.org/forum/viewtopic.php?f=5&t=111](http://blueman-project.org/forum/viewtopic.php?f=5&t=111)

Unfortunately, it still hasn't helped me get my headphones working with Intrepid. I have just given up for now.

If you find out anything, post it back to this thread, because I will get an e-mail when a new message is posted here. Hopefully you or someone else will finally figure out what is wrong.

---

### Post by markbuntu on 2009-03-25
According to Lennart, the lead pulse developer, you need the latest git from bluez to get your bluetooth working with pulse without crashing. There is some discussion about this on the pa mailing list.

---

### Post by John Jason Jordan on 2009-03-26
> **markbuntu said:**
> According to Lennart, the lead pulse developer, you need the latest git from bluez to get your bluetooth working with pulse without crashing. There is some discussion about this on the pa mailing list.

I can't get to the pulseaudio mailing list because Firefox says the certificate is self-signed and not valid. I suppose I could figure out a workaround, but can you just tell me where to get the latest git and where to find the how-to for installing it?

---

### Post by markbuntu on 2009-03-26
I think you can find that at bluez.org.

---

### Post by ndale686738 on 2009-04-15
I downloaded the latest bluez components from
[HTML]http://philip.magicalforest.se/dists/intrepid/extra/[/HTML]
and then the "pactl load-module module-alsa-sink" command loaded the module properly and i could see the device in pavucontrol.

my .asoundrc file looks like this

```
pcm.bm {
    type bluetooth
    device 00:19:7F:13:75:EC
    profile "voice"
}
pcm.bs {
    type bluetooth
    device 00:19:7F:13:75:EC
    profile "hifi"
}
```

use the "bs" device for stereo audio on your music player, just use pavucontrol to redirect the stream once the player is running. You can use the "bm" device for two way mono audio for skype or other two way streams. 

for some resason pulseasudio crashes if i try to load the alsa-source module for the "bs" device, but it works fine without it loaded so i just dont load it.

for any newb's the full commands are
```
pactl load-module module-alsa-sink device=bs
pactl load-module module-alsa-source device=bs
```

you can name the devices whatever you want, just change it in the .asoundrc and the reference in the pactl command. 

if puseaudio crashes restart it with
```
pulseaudio -k; pulseaudio -D
```

hope it helps

---

### Post by Xsoldier2000 on 2009-05-13
I found this thread after playing around with this for a couple months.

[http://forums.overclockers.com.au/showthread.php?t=780054]("http://forums.overclockers.com.au/showthread.php?t=780054")

It worked perfectly for me using the included bluetooth manager included with Jaunty x64.

I had to uninstall blueman to completely to make everything work. The only thing that bugs me is I have to do four steps every time I restart/logout...but I don't nneed to go back into windows just to use my S9's now. I'm excited.

Hope this helps others.

BIG thanks to HyRax1 over at the overclockers forum for this!

---

### Post by markbuntu on 2009-05-15
If you have the following bluetooth should work for you OOB and be easily controlled in the pulseaudio volume control

bluez 4.35 or later
pulseaudio 0.9.15
alsa0.9.19 or later
gnome bluetooth 2.27.4

---

### Post by Skybinary on 2009-06-11
I had quite a few headaches with bluetooth, but since a clean install of jaunty all i had to do was create an .asoundrc file as others have.

I decided to tweak that file some.  I totally remastered it and for the most part it is working for me, issues i have are when the headset is offline, charging or just not used.  Then i have to make a minor alteration in the .asoundrc to fix that.

Here is what i have tweaked to work, with the last 2 lines I switch the comment, depending if I want sound from speakers or headset...

```
ctl.bluetooth_hwc { type bluetooth device 00:0D:FD:10:9D:73 profile "auto" }
pcm.bluetooth_hwv { type bluetooth device 00:0D:FD:10:9D:73 profile "voice" }
pcm.bluetooth_hwh { type bluetooth device 00:0D:FD:10:9D:73 profile "hifi" }
pcm.btheadset { type plug slave { pcm "bluetooth_hwv" } }
pcm.btheadphones { type plug slave { pcm "bluetooth_hwh" } }
pcm.!default { type plug slave { pcm "bluetooth_hwh" } }
#pcm.!default { type hw  card 0 }
```

When i use the pactl load module the volume control houses my bluetooth device but all of the controls have zero to no affect.

Lately i found by adding the ctl.bluetooth... line i can use the headset navigation buttons to activate macros using keyboard short-cuts found in system-preferences. I currently use the FFWD button to turn off my monitors.

What is pulse, what does it do, i have no idea, i have tinkered periodically and get no-where quite quickly.

---

