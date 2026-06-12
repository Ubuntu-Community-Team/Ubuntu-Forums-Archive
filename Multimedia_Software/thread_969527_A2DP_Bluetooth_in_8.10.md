---
title: "A2DP Bluetooth in 8.10"
date: 2008-11-03
forum: Multimedia Software
---

### Post by idingsdale on 2008-11-03
Hi All,

I am trying to set up a bluetooth A2DP device (A belkin tunestage RX) with my Ubuntu 8.10 installation.

I have seen several guides on doing this, but they all seem to refer to older versions of pulseaudio/bluez than in 8.10.

Hcitool and the GUI see the device but I am unable to pair with it. The GUI tries to use a PIN of 0000 and gives no option to change it, but the device has a fixed code of 1111. 

Has anyone set up a stereo bluetooth device in 8.10?

---

### Post by lavadisco on 2008-11-03
Bump. I'm having the same issue. Would love to get A2DP working. Didn't work for me in Hardy either.

---

### Post by rablack on 2008-11-04
Hi,

On the plus side, the actual bluetooth stack in Intrepid worked out of the box with my hardware, and after pairing with my phone I can browse the memory card in it as though it is a connected disk! Very impressive!

However, like the OP, I'd also like to know how to get an a2dp devicde to work with Intrepid. I have tried following the steps in the guides for Hardy (eg [this one at overclockers.com.au]("http://forums.overclockers.com.au/showthread.php?t=694010")), but have had no success. 

So far I have successfully paired my headphones by using sdptool to browse for services. However, I can't work out what to do next! According to the Hardy guides you create an audio sink in PulseAudio. I get an error message when using the command given for Hardy (pactl load-module module-alsa-sink device=bluetooth and
pactl load-module module-alsa-source device=bluetooth). With the new GUI wizard to find devices, it would be very helpful if there was something similar to show the available services, and possibly some information on how to use the various profiles.

Thanks,

Richard

---

### Post by md20/20 on 2008-11-10
I hate me-too posts, but I have the same issue. Is there any hope of having the A2DP Intrepid Bluetooth issue resolved anytime soon?

---

### Post by rablack on 2008-11-10
Hi,

I have recently been successful in getting a2dp to work. Mostly. 

The main thing that I think was causing problems was using the word "bluetooth" for the name of the audio connection in the .asoundrc file. Changing it to something else (more descriptive and useful, eg moto_ht820) seems to have worked. I don't know if "bluetooth" is a reserved word, but I am now able hear sounds in my headphones.

For the OP, I should mention that I was presented with a pairing PIN code entry balloon when I used the command sdptool browse [mac address], although this did not work initially - perhaps there has been an update?

The "mostly" in my first sentence is down to the following:

1) The headphones do not enter standby/sleep/whatever mode when sound stops playing - using Ubuntu's default Totem movie player causes a constant hiss in the headphones  until the application is closed.

2) I have been unsuccessful in automating the process to add the audio sinks and sources to pulseaudio and set them as default. It requires manually running a script to load the pulseaudio modules and then manually clicking on the pulseaudio device chooser and typing in the names. A command to add to the script  to do the last part would be great. Even better if it can be totally automatic - I am going to investigate the bluemon package as this looks promising.

Hope this helps,

Richard

---

### Post by md20/20 on 2008-11-11
Changing the .asoundrc name of the device from 'bluetooth' to 'moto_s9' helped, thanks.

Afterwards I had to delete the preexisting pairing from the Bluetooth Manager applet and re-pair it. (I used the 'sdptool browse' method to force the pairing.)

I still have the same issue as you with having to manually set the default source and sink using the PulseAudio Volume Control, but that's where I was with Hardy too so essentially I'm back in business for now.

---

### Post by rablack on 2008-11-11
Glad that helped!

I've found [http://blueman.tuxfamily.org/]("http://blueman.tuxfamily.org/") which looks like an enhanced GUI for bluetooth in Ubuntu, but it  it works with the older v3 Bluez stack. I haven't installed it yet, as I suspect putting the old stack might break a2dp.

If I could program, I'd be very tempted to start work on something like this!

Richard

---

### Post by j4ni on 2008-11-15
Hi, 

I'm trying to use my Nokia bluetooth handsfree with skype. I'm unable to add sink/source to PulseAudio. I have changed .asoundrc device name to nokia_hf but I still get an error when running commands "pactl load-module module-alsa-sink device=nokia_hf" and "pactl load-module module-alsa-source device=nokia_hf" (Failure: Module initalization failed). 

I have paired my bluetooth handsfree using Gnome Bluetooth Applet.
I have also modprobed following modules snd_bt_sco and modprobe sco.

Rablack after you changed asoundrc device name were you able to perform pactl load-module module-alsa-sink device=xxxxxx without any errors? Did you skip steps 1-12 when following HyRax1's howto ( [http://forums.overclockers.com.au/showthread.php?t=694010](http://forums.overclockers.com.au/showthread.php?t=694010) )? Does /etc/bluetooth/hcid.conf exist in your system? If it does exist could you paste the content here?

Thanks

-j4ni

---

### Post by rablack on 2008-11-15
Hi j4in,

I did not use steps 1-11 in the overclockers guide, I just used the bluetooth preferences app that is in Intrepid. However, I did use step 12 - "hcitool scan" - to retrieve the mac address of my bluetooth headphones, as this is not shown anywhere else. 

I do not have etc/bluetooth/hcid.conf on my system.

I think the thing that I did to get this to work is that once I paired my devices using the bluetooth preferences app, I used "sdptool browse xxxxxxxxxxxx" to initiate a connection to the headphones. At this point I got a PIN request balloon. After this I was able to successfully load the pactl modules. I think this would work with any program that tries to create a connection. I am guessing that the pactl load-module command requires authentication to have already occured.

Hope this helps,

Richard

---

### Post by lordfoul on 2008-11-16
Anyone try this [PulseAudio]("http://fosswire.com/2008/10/25/better-bluetooth-audio/") work around?  Bit of a Kludge but hey if it works.

---

### Post by rablack on 2008-11-16
Hmm, looks almost identical to the overclockers thread I used, apart from a bit more detail on using pulseaudio to move sound from already running applications (actually very useful) and a bit at the end which might get AVRCP working (I haven't tried that yet myself). Looks like this is "the" method for now!

I read a blog on the bluez site (from August I think) that talked about adding a wizard or gui for A2DP devices and pulseaudio. Hopefully that isn't far off...

I'm still having trouble finding a command to use in a script to set the default pulseaudio output. Most things I have tried so far result in an error message stating that the deamon is already running. Does anyone have any suggestions?

Thanks,

Richard

---

### Post by lavadisco on 2008-11-26
Where is .asoundrc on my system? I can't find it.

---

### Post by priegog on 2008-11-29
> **lavadisco said:**
> Where is .asoundrc on my system? I can't find it.
In your home folder. You have to do a Ctrl + H to show the hidden files and folders.

---

### Post by lavadisco on 2008-11-29
> In your home folder. You have to do a Ctrl + H to show the hidden files and folders.

Still don't see it even when I make the hidden files appear. Is there a specific piece of software I need to have installed before I'll have that file?

---

### Post by priegog on 2008-11-29
> **lavadisco said:**
> Still don't see it even when I make the hidden files appear. Is there a specific piece of software I need to have installed before I'll have that file?

No. That file is not there by default. If you don't have one, just create one. Open the text editor and put in the things that need to be in that file, and then save it with that name (including the dot in front of the name) in your home directory (if you browse from the root of the filesystem it is /home/yourusername/

---

### Post by thoman on 2008-12-31
I found this [thread]("http://www.board4all.cz/showthread.php?t=134759") and it works fine with my S10 and Sony Ericsson HBH-DS200 

worth trying...

---

### Post by Paul133 on 2009-01-03
The first thread worked flawlessly with me once I changed "bluetooth" to "btheadset" and skipped steps 1-11. Now I just need to get AVRCP working!

---

### Post by John Jason Jordan on 2009-01-12
> **thoman said:**
> I found this [thread]("http://www.board4all.cz/showthread.php?t=134759") and it works fine with my S10 and Sony Ericsson HBH-DS200. worth trying...

I tried the nstructions on that thread and couldn't get past the first line where it said to install bluetooth-alsa:

jjj@Devil7:~$ sudo apt-get install bluetooth-alsa
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package bluetooth-alsa is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package bluetooth-alsa has no installation candidate

I have just about all repositories enabled and Synaptic shows 26,000+ packages, so I don't know why apt can't find it. Maybe it's in a Hardy repository?

I've been working for two days trying to get my Sony BT50 audiophile headphones to work in Intrepid. They worked fine in Hardy, but nothing I have tried has succeeded in getting sound to them in Intrepid from any application.

They do appear paired up in the bluetooth applet (bluetooth icon in the Gnome panel). Unfortunately, there are no instructions for what the icons in that GUI mean:

[IMG]http://web.pdx.edu/~johj/bluetooth.png[/IMG]

Maybe if there was some documentation I could figure it out. :(

Meantime, I have tried all the instructions in this thread without success.

---

### Post by brianpeiris on 2009-01-23
John: 
Try skipping the bluetooth-alsa install. It worked for me with my Etymotic Research Ety8 ( ER88 ) headphones.

Unfortunately I can't get it to work with VLC, so I'm stuck playing my files with Totem, any solutions for this problem?

Edit: Flash audio in Firefox doesn't work either :(

---

### Post by John Jason Jordan on 2009-01-23
> **brianpeiris said:**
> John: 
Try skipping the bluetooth-alsa install. It worked for me with my Etymotic Research Ety8 ( ER88 ) headphones.

Unfortunately I can't get it to work with VLC, so I'm stuck playing my files with Totem, any solutions for this problem?

Edit: Flash audio in Firefox doesn't work either :(

I can't get my bluetooth headphones to work with anything. They worked fine in Hardy, but after upgrading to Intrepid I have not heard so much as a pop, whistle or click from them. The sound works fine, it just comes out of the speakers. 

The headphones are paired and connect just fine. The problem is on line 18 of the overclockers how-to - the pactl commands. The pactl commands hang pulseaudio so hard I have to use kill -9 to finish it off so I can restart it. Strace just stops when it hangs - no error messages or clues. There are no error messages anywhere else that I have found. I followed the advice to use "btheadset" in the .asoundrc file, and then changed all commands from "bluetooth" to "btheadset," but it still hangs on the pactl commands.

I wanted to post on the overclockers board, but the site won't let me register with a gmail e-mail address. 

I also tried bluetooth-alsa, although I had to install the package manually and find its dependencies myself as well. But it didn't make any difference.

I think it might work if I could just figure out why the pactl commands hang pulseaudio.

---

### Post by brianpeiris on 2009-01-23
Yeah, I'm not even going to try messing with pulse-audio. I'm afraid I might loose sound altogether if I tinkered around too much.
Unless someone posts a quick fix, I'm just going to wait it out and let the problem solve itself (Hopefully in Jaunty!)

Can't really complain, Ubuntu works flawlessly for everything else I do, wireless audio is a convinience I can live without.

You should try the [board4all.cz thread]("http://www.board4all.cz/showthread.php?t=134759") again if you don't mind beind limited to Rhythmbox and Totem.
(Make sure you insert your device's MAC address in all the required files -- three inserts altogether -- that got me the first time I tried)

Goodluck!

---

### Post by John Jason Jordan on 2009-01-23
> **brianpeiris said:**
> Yeah, I'm not even going to try messing with pulse-audio. I'm afraid I might loose sound altogether if I tinkered around too much.
Unless someone posts a quick fix, I'm just going to wait it out and let the problem solve itself (Hopefully in Jaunty!)

Can't really complain, Ubuntu works flawlessly for everything else I do, wireless audio is a convinience I can live without.

You should try the [board4all.cz thread]("http://www.board4all.cz/showthread.php?t=134759") again if you don't mind beind limited to Rhythmbox and Totem.
(Make sure you insert your device's MAC address in all the required files -- three inserts altogether -- that got me the first time I tried)

I tried the Board for All thread. No error messages as I followed the instructions, and I entered the MAC address in all three files, but still no sound from the headphones. :(

Back to the pulseaudio problem: If I could just get the pactl commands to work without hanging pulseaudio I could probably get it to work. The problem is that pulseaudio does not know my headphones exist. And it's not going to learn about them until I can get those pactl commands to work.

---

### Post by i.am.technofreak on 2009-09-13
Howdy

That pulseaudio fix works great for my, im running 9.04.  Its really cool cos i pulled my BT headsphones apart and soldered a 3.5mm socket on, and now I can listen to my grooveshark from the other side of the room on the good lounge speakers!!! thanks for the link!!!!  

ps pavucontrol is quite a cool app

---

