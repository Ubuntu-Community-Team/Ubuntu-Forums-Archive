---
title: "How I got my bluetooth stereo speakers working on intrepid"
date: 2009-04-14
forum: Multimedia Software
---

### Post by natrixnatrix89 on 2009-04-14
So I'm kinda newbie and wanted to get my bluetooth working. When I searched the forums all I could find was people complaining about their problems.
So first thing I did was I updated bluez.
to do so add ```
deb http://ppa.launchpad.net/blueman/ppa/ubuntu intrepid main
deb-src http://ppa.launchpad.net/blueman/ppa/ubuntu intrepid main
``` to your sources (system>Administration>Software Sources>Third Party Software>Add)
then run ```
sudo apt-get update
sudo apt-get upgrade
```.
Now plug in or turn on your bluetooth adapter, put your bluetooth headphones or stereo in pairing mode and find the mac address of your bluetooth audio device by typing in terminal ```
hcitool scan
```
It will now scan and list the bluetooth devices near you. find your headset and copy it's mac by pressing ctrl+shift+c. For me it was 00:18:E4:06:AE:D0.
Now run ```
sudo gedit ~/.asoundrc
``` and paste
```
pcm.bluetooth {
  type bluetooth
  device XX:XX:XX:XX:XX:XX
  profile "auto"
}
``` in it. Replace XX:XX:XX:XX:XX:XX with the mac of your bluetooth audio device. save the file and close.
The next thing you have to do is to set up your player to use bluetooth. you can read about it in [here]("http://wiki.bluez.org/wiki/HOWTO/AudioDevices#SupportedPlayers")
In my case I use only rhythmbox and totem, so it might be convenient to make a script that would switch my players between normal speakers and bluetooth. To switch TO using bluetooth we'll create script by typing
```
sudo gedit ~/.SwitchToBluetooth
``` It will open text editor. now paste ```
#!/bin/bash
gconftool -t string -s /system/gstreamer/0.10/default/musicaudiosink "alsasink device=bluetooth" &
``` in it and save and close. run ```
sudo chmod +x ~/.SwitchToBluetooth
```.
Now create a script to switch back to normal
```
sudo gedit ~/.BackToNormal
``` and paste ```
#!/bin/bash
gconftool -t string -s /system/gstreamer/0.10/default/musicaudiosink "autoaudiosink" &
``` in it. save, close and run ```
sudo chmod +x ~/.BackToNormal
```
Now we have two scripts that switch totem and rhythmbox to and from using bluetooth. Now look at your desktop and create launchers (right click>create launcher) Enter the name "switch to bluetooth" and enter the command /home/<your username>/.SwitchToBluetooth
and you can create a similar command to switch back to normal - add the command /home/<your username>/.BackToNormal

Yay. Now we are ready to pair with your headset. Now click on the launcher "switch to bluetooth" open totem or rhythmbox (alt+F2 and type rhythmbox) and put your bluetooth device in pairing mode again. The bluetooth icon will start blinking. click on it and enter the pin of your device (should be 0000 or 1234) It might ask you to enter it again - if so, enter it again. Then it will ask for authorisation - tick always allow and click yes. now switch to your music player and double-click on a song to start playing. Now it should be playing. If it isn't maybe your headset doesnt support a2dp. Or theres just a glitch this time - so just try turning your audio device on off again - enter the pin again and try to get it working (I had to try restarting the bluetooth stereo a couple of times before i got it working)
Now when you want to use normal speakers again just use the launcher you created to switch back to normal. and we're done :)
Some audio files might sound choppy so wiki.bluez.org suggests
> You may get choppiness with a2dp. An hcid.conf with "lm accept,master;" and "lp hold,sniff,park;" will be more robust. 
I don't know how to do this on intrepid. I know there was such a file un hardy, but cant find it in intrepid. Maybe someone smarter can tell me about it. But mostly everything works smooth :)

---

### Post by strider22 on 2009-04-20
Nice contribution!

---

### Post by minor ubuntoid on 2009-06-21
Thanks for this.

I don't think you need to use sudo to edit any of those files, though. You shouldn't need the ampersand on the end of your gconftool lines either.

---

