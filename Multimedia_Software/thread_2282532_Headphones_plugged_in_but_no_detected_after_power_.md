---
title: "Headphones plugged in but no detected after power outage"
date: 2015-06-15
forum: Multimedia Software
---

### Post by manny9 on 2015-06-15
I had to use usb headphone's borrowed,now i dont have them anymore,so the green and pink ports dont detect what i plug into them,please help,i have done a bit of troubleshooting  like alsa mixer,but its not detecting the headphone's or speaker's or anything i put into those port's

---

### Post by Bucky Ball on 2015-06-15
Try with Pulseaudio Volume Control. Install it from Software Centre or Synaptics (or a terminal, 'pavucontrol' from memory) if it isn't installed already, then launch it. Open the playback tab and get an audio stream going (play some music). You should see the stream in the Playback tab. If so, tweak with the output device. You can also look in the Output tab and Configuration tab. Might have something off or wrongly routed there. 

Always include the Ubuntu release and flavour you are using when posting and anything you've done to try and remedy the situation. It will improve your chances of support. Thanks and let us know how you go.

---

### Post by manny9 on 2015-06-15
Yeah it's ubuntu 14.10 64bit, that didn't work because it doesnt detect my headphones when i put them in i tried all the options,for instance when i put my usb headphone's in it says logitech-mediadevice

thanks for the reply

---

### Post by Bucky Ball on 2015-06-15
It is not going to give you the brand and model if you are plugging in the headphones via regular mini-jacks. You should be setting PAVControl to 'Headphones'.

If you've changed anything in Alsamixer, change it back to what it was to start and try PAVControl. Don't wait to see the model of your headphones if they are 'mini-jacked' into the machine. Just choose 'heaphones' or your analogue input (not digital or HDMI or USB, in fact, make sure the USB headphones are out so they don't appear as an option ... avoid confusion).

---

### Post by manny9 on 2015-06-15
PAVcontrol give's me 2 options, no headphone option,one is my graphics card and built in digital stereo(IEC958),which use to work,now doesnt no output and before when i plugged in  aheadphone or speaker's it would display it as soon as i plug it in now nothing happens,except with usb headphone's

---

### Post by Bucky Ball on 2015-06-15
You are seeing your graphics card in Pulse Audio Volume Control???

---

### Post by manny9 on 2015-06-15
Yeah but it's not important it's called BARTS hdmi Audio [radeon Hd 6800 series] Digital Stereo (Hdmi)  The one which use to work is Built in Audio Digital Stereo (IEC958)
 those are the only two possible outputs

---

### Post by Bucky Ball on 2015-06-15
Ok, in the Configuration tab in PAVControl, set the Built in Audio to 'Analogue Stereo Duplex'. The option should be in the drop down list next it. Does the option for it appear in Playback or Output now? You may need to restart Pulse for this to happen.

---

### Post by manny9 on 2015-06-15
i set the Built in Audio to 'Analogue Stereo Duplex' it didn't work so i tried all,nothing worked (while i played a youtube video with audio) i was mentioning how it has a headphone's unplugged output option in output device's is that important,if my headphone's are plugged in,it shouldn&#8217;t count it unplugged or have that option

---

### Post by manny9 on 2015-06-15
Thought it would be nice to include in alsamixer my headphone's arent detected[IMG]http://gyazo.com/0b24b6a3eeabb24c5232a1c54c236f22[/IMG]

took a screenie:
[http://gyazo.com/0b24b6a3eeabb24c5232a1c54c236f22](http://gyazo.com/0b24b6a3eeabb24c5232a1c54c236f22)

---

### Post by Bucky Ball on 2015-06-15
In your screenshot of Alsamixer, I'm guessing you can't use the right arrow key to get to the headphone entry, then the up arrow to turn it up?

---

### Post by manny9 on 2015-06-15
Nope,ive tried muting and un muting and checked alot of stuff

---

### Post by Yellow Pasque on 2015-06-15
The first thing I would try is resetting the pulse configuration. Sometimes, it gets corrupted and needs to be (automatically) regenerated:
```
rm -r ~/.config/pulse*
```
Then, log out and back in. If that doesn't work, you may want to google for a little utility called 'hdajacksensetest' to see if the driver detects you plugging stuff into the sound jacks. If it doesn't, something may have been damaged in the power outage, or you may need to go into your BIOS, disable the audio codec, boot, go back into the BIOS and enable the codec.

> The one which use to work is Built in Audio Digital Stereo (IEC958)
Probably not. The headphone jack is not a digital output. More likely, you used to have an option to select Analog Output which has disappeared for some reason (and then once you selected that option, you would have another option for stereo or headphone profile).

> **manny9 said:**
> in alsamixer my headphone's arent detected

The only thing the screenshot shows is that your headphones are unmuted and don't have a separate volume control. Unless you're certain that they had a separate volume control before, that is not concerning/unexpected.

---

### Post by manny9 on 2015-06-15
I couldnt find hdajacksensetest' even by googling.i did find something else, i disabled audio in bios and re enabled, to no avail..i only found hdajackretask but i didnt know what to do with it.I ran the command to  reset pulse configuration aswell,no difference...when i plug in my headphone all i hear is extreme static not too loud,but when i scroll down and stuff it give's off a tiny reaction on the screenie i showed you it was not muted,it just wasn't there...Do you guy's think a fresh install of ubuntu or driver's will fix this? i know the audio is working but only with usb devices i want to use the green jack but it doesn't detect anything maybe i need help with the hdajacksensetest

---

### Post by manny9 on 2015-06-16
Bump,Please help me someone

---

### Post by manny9 on 2015-06-17
bump

---

### Post by Bucky Ball on 2015-06-17
Out of ideas here, but I can help by telling you that and bumping the thread. :)

---

### Post by Yellow Pasque on 2015-06-17
The hdajacksensetest utility is here in the snd-hda-tools package: [https://launchpad.net/~diwic/+archive/ubuntu/hda/+packages](https://launchpad.net/~diwic/+archive/ubuntu/hda/+packages)
You can add the whole ppa or download the .deb directly: [https://launchpad.net/~diwic/+archive/ubuntu/hda/+files/snd-hda-tools_0.20130207%2Btrusty1_amd64.deb](https://launchpad.net/~diwic/+archive/ubuntu/hda/+files/snd-hda-tools_0.20130207%2Btrusty1_amd64.deb)

Then run it (as root/sudo). The numbers you use for -c and -d depends on what soundcards you have installed. Look in /dev/snd to see what hwC#D# are available
```
./hda-jack-sense-test.py -c 1 -d 3
Pin 0x14 (Green Line Out): present = No
Pin 0x15 (Black Line Out): present = No
Pin 0x16 (Orange Line Out): present = No
Pin 0x17 (Grey Line Out): present = No
Pin 0x18 (Pink Mic): present = No
Pin 0x19 (Pink Mic): present = No
Pin 0x1a (Blue Line In): present = No
Pin 0x1b (Green HP Out): present = No
```
So I plug my headphones into one of the jacks (orange in this case) and run it again:
```
Pin 0x14 (Green Line Out): present = No
Pin 0x15 (Black Line Out): present = No
Pin 0x16 (Orange Line Out): present = Yes
Pin 0x17 (Grey Line Out): present = No
Pin 0x18 (Pink Mic): present = No
Pin 0x19 (Pink Mic): present = No
Pin 0x1a (Blue Line In): present = No
Pin 0x1b (Green HP Out): present = No
```

---

### Post by manny9 on 2015-06-17
Before i installing thait it gave me Package operation failed so i did>  sudo apt-get update and got these error's which may be importantand at the end it always fail's to fetch these 

W: Failed to fetch [http://ppa.launchpad.net/diwic/jack-detection/ubuntu/dists/utopic/main/binary-amd64/Packages](http://ppa.launchpad.net/diwic/jack-detection/ubuntu/dists/utopic/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/diwic/jack-detection/ubuntu/dists/utopic/main/binary-i386/Packages](http://ppa.launchpad.net/diwic/jack-detection/ubuntu/dists/utopic/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/utopic/main/binary-amd64/Packages](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/utopic/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/utopic/main/binary-i386/Packages](http://ppa.launchpad.net/ubuntu-audio-dev/ppa/ubuntu/dists/utopic/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by Bucky Ball on 2015-06-18
Go to 'Software and Updates' (should be called something like that in Ubuntu) and untick or remove the offending repositories. They are either down or broken.

---

### Post by Yellow Pasque on 2015-06-18
Oh, I didn't see you were using Utopic/14.10. Yeah, the PPA hasn't added packages for anything beyond 14.04. Still just downloading and installing the package for Trusty should work: [https://launchpad.net/~diwic/+archive/ubuntu/hda/+files/snd-hda-tools_0.20130207%2Btrusty1_amd64.deb](https://launchpad.net/~diwic/+archive/ubuntu/hda/+files/snd-hda-tools_0.20130207%2Btrusty1_amd64.deb)

---

### Post by Bucky Ball on 2015-06-18
Nice one. Fingers crossed that works.

If it does, the other, more permanent but more work option, is to install 14.04 LTS as 14.10 has about a month and some support life left. Then an upgrade will be required in any case. You could try 15.04 and see if it works or is fixable on that, about seven months support. Installing 14.04 LTS if it works, at least, would guarantee support for five years, until 2019, which means you would be, hopefully guaranteed it will continue to work that long (theoretically~!). :)

---

