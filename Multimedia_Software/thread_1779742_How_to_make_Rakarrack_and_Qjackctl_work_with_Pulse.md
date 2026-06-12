---
title: "How to make Rakarrack and Qjackctl work with PulseAudio"
date: 2011-06-10
forum: Multimedia Software
---

### Post by gbd on 2011-06-10
This post may help those who want to use Rakarrack to make their guitars sound awesome. Thanks to the people behind Rakarrack. It's a wonderful thing. 

I am using onboard sound. I also have a firewire interface, but using that is a another story... 

I had some difficulty in finding out what needs to be done to make everything work on my vanilla install of Natty.

First install Rakarrack through the Ubuntu Software Centre or Synaptic, whichever you prefer. This will also install QjackCtl, the front end for jackd (and some other, required packages). I made sure I ticked the option for realtime when prompted.

Once this is done, it is important to start QjackCtl first, by searching in the Applications menu and clicking on the button. Then start Rakarrack in the same way and everything should be fine by default. I have added both buttons to the Unity Launcher to make things easier in future.

If QjackCtl doesn't start, it means you will have to fiddle with the settings in Setup. I set the Frames/Period to 128 @ a Sample Rate of 44100, giving me a latency of 5.8msec. This seems acceptable to my ears anyway, with no xruns unless I start other programs. See [this page]("https://help.ubuntu.com/community/HowToJACKConfiguration") for a quick run-through on how to configure QjackCtl.

I also wanted to be able to play along with videos and mp3s, so I had to do some more tweaking to get PulseAudio to work with QjackCtl. 

First, I installed 'pulseaudio-module-jack' through Synaptic. I entered these commands into the terminal (Ctrl-Alt-T) one after the other to reload PulseAudio with the new settings:

```
pulseaudio --kill
pulseaudio --start

```
Then I tweaked QjackCtl settings. In Setup->Options:

1. Tick 'Execute script after Startup' and paste this into the box:

```
pactl load-module module-jack-sink channels=2; pactl load-module module-jack-source channels=2; pacmd set-default-sink jack_out; pacmd set-default-source jack_in
```

2. Tick 'Execute script on Shutdown' and paste this into the box:

```
pulseaudio -k
```

3. Tick 'Execute script after Shutdown' and paste this into the box:

```
killall jackd; pulse-session
```

4. Click OK and restart QjackCtl for settings to take effect.

QjackCtl starts with 'system' and 'PulseAudio JACK' appearing in the Connections tab. I find I have to manually connect 'system' to 'system' in the Connections tab to hear my guitar. Videos, mp3s, YouTube and Rakarrack all work beautifully. After I quit QjackCtl, PulseAudio restarts and sound works as normal.

Note: As mentioned above, it is important to start QjackCtl before starting Rakarrack. It is also important to 'Disconnect All' in the Connections tab before firstly stopping QjackCtl, then clicking Quit.

I have looked at so many posts while searching for this solution, none had everything I needed but all helped immensely. If you recognize aspects of your solution here, then thanks!

---

### Post by gbd on 2011-06-13
After a bit of playing around I followed the advice in [this link]("http://fossplanet.com/f10/module-jackdbus-detect-pulseaudio-84602/") and ticked 'Enable D-Bus interface' under Setup->Misc in QjackCtl. I now find I can stop QjackCtl without having to 'Disconnect All' first. PulseAudio restarts, then QjackCtl opens the next time with 'system' connected to 'system' and everything is ready to go.

EDIT: this behavior does not persist after a reboot. I still have to manually connect 'system' to 'system' in the Connections tab of QjackCtl to hear my guitar. It's weird, I've started and restarted QjackCtl several times and sometimes it will start with all connected, and sometimes it won't. Sometimes it will quit by itself when I click 'Stop' and sometimes it waits until I click 'Quit'. I've tried clicking 'Disconnect All' before clicking 'Stop' and tried just clicking 'Stop' but I can't seem to get consistent behavior. Regardless, everything still works.

Maybe a guru will stop by and let me know what's going on...

---

### Post by gbd on 2011-07-13
By the way, make sure you have something plugged into your sound card (internal integrated chip in my case). I unplugged the mono guitar jack to mini-stereo jack adapter to take to a gig. Qjackctl stopped working. Wouldn't connect, error messages, nothing I tried worked. Until I remembered the adapter. Plugged it back in, fired up Qjackctl, all back to normal.

Hope this helps someone.

---

