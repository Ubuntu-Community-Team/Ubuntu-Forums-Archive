---
title: "Volume keyboard control in Gnome?"
date: 2006-08-29
forum: Multimedia &amp; Video
---

### Post by khedron on 2006-08-29
I have an Audigy Soundblaster and am using the alsa mixer for it. It works well, but I have one problem: the volume key on my keyboard (Logitech cordless) controls the onboard Intel master volume. It is set up using System>Preferences>Keyboard Shortcuts (in Gnome).

How can I set Gnome to use the Soundblaster when controlling volume rather than controlling the onboard sound?

---

### Post by hopstah on 2006-08-30
maybe you could disable the onboard sound via your bios - unless you feel the need for both sound cards.

---

### Post by RSL on 2006-12-06
Did you find a solution to the problem? I've got a similar situation. Same setup basically. I did manage to disable the onboard sound but there's still the IEC958 outputs on the Audigy. At first I couldn't even get the volume control on the panel to control the analog but I eventually found the preferences and changed it from the digital [IEC958] to the analog. I presume something like this needs to be done with the keyboard mappings. Anyone?

---

### Post by khedron on 2006-12-08
In Kubuntu you have to install "keytouch", and then run it and select which keyboard model you have and maybe change the default actions. If you do that, it's best if your keyboard is plugged into the keyboard socket (rather than the USB), as more keys can be used. This is something to do with the Linux kernel not fully supporting USB.

In GNOME there was a keyboard shortcuts customiser in the System menu, and you could set Volume Up and Down keys.

Sorry if I am unhelpful; I switched to Kubuntu for the latest release.

---

### Post by wilberfan on 2006-12-14
I have a similar issue.   I set up the volume keyboard shortcut, and I get an icon that shows the volume increasing or decreasing--but there is no change in actual sound levels.

---

### Post by RSL on 2006-12-14
That one's easy to fix. Just right click the volume widget and under preferences manually set the device to use.

---

### Post by wilberfan on 2006-12-15
> **RSL said:**
> That one's easy to fix. Just right click the volume widget and under preferences manually set the device to use.

No, I understand that...   Under Edgy, when you set a volume up or down keyboard shortcut, there's a window that pops up in the exact center of the screen (it's got a speaker symbol) when you use the shortcut.   One of my Edgy boxes shows that icon in the center of the screen, and indicates that the volume is increasing...but the actual sound levels remain unchanged...

(It's weird, but it works OK on my OTHER Edgy box...)

---

### Post by RSL on 2006-12-15
Ah, then I have [still] the same exact problem.

---

### Post by StarQuake on 2006-12-19
> **RSL said:**
> I presume something like this needs to be done with the keyboard mappings.

That was exactly what I was thinking, did you find a solution yet?

---

### Post by ryscar on 2006-12-30
Just throwing in a "me too" here.  I have the same problem and am unable to find a solution.  Any help would be great.

Thanks,
Ryan

---

### Post by CyberCod on 2007-02-04
same here, popup sound slider seems to be using the onboard.  I'll disable it upon next reboot, and let you guys know if that fixed it.

I'd like to know what program controls that popup.  I'd like to just be able to configure it.  But watching in System Monitor while pushing it shows no changes, so obviously its something that is running all the time.  Maybe tied into X or Nautilus or something like that.

Having two soundcards is a plus for me, but the wife likes the multimedia keys.

Grrr...

---

### Post by RSL on 2007-02-04
[Late reply] I never figured out a solution. I can't even get the onboard soundchip to disable. It still shows up no matter what I do. :( I miss my volume control.

---

### Post by isecore on 2007-02-11
Just adding that I've got the exact same problem. Volume control worked fine but for some arcane reason it decided to stop.

Now it's like every one elses problem: I push the keys, the small popup shows up and makes bold claims to changing the volume, but the speakers sound the same. Also, when checking with the volume control nothing has happened. Manual volume through the volume control i Gnome works fine btw, as do the widget in the deskbar. It's just that darn popup that doesn't work.

My guess is that it's controlling the volume of something else. Ubuntu identifies several soundsources in my system - my Audigy2 ZS as well as my Logitech Camera as well as my onboard sound (which IS disabled in BIOS but none the less shows up).

This is annoying the hell out of me! Apparently this will be fixed in Feisty Fawn, but I don't want to wait two months for something that there should be a fix for now.

EDIT: I fixed it at least for me. The problem was that the onboard soundcard was claiming first slot. I changed /etc/modprobe.d/alsa-base and added "options [my onboard-sound driver] index=-2" thereby forcing it to choose a higher slot and make my Audigy the default card. Now the keyboard volume works fine (for me) :)

---

### Post by dmik on 2007-03-04
Feisty users can find this link [https://help.ubuntu.com/community/MultimediaKeys#AssigningTracksToKeys]("https://help.ubuntu.com/community/MultimediaKeys#AssigningTracksToKeys") to be useful -- it seems that this problem was nicely fixed in Feisty. There is also some info about Edgy, but I'm afraid it won't be very helpful.

---

### Post by jimbopouliot on 2007-03-06
It's a bug in GNOME that has been corrected recently and is fixed if you use Feisty Fawn (apparently). See the bug information at: [http://bugzilla.gnome.org/show_bug.cgi?id=173035](http://bugzilla.gnome.org/show_bug.cgi?id=173035)

In Edgy Eft (6.10) and earlier, the volume keyboard bindings will only control the first channel on the first sound device found. The problem is there is no way to configure this, neither graphically nor through the console and configuration files.

If you want to control the first channel of a rather normal sound card, you can try modifying the order in which they are detected. See [http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide#Configuring_default_soundcards_.2F_stopping_soundcards_from_switching](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide#Configuring_default_soundcards_.2F_stopping_soundcards_from_switching)
This will not work with USB sound cards though (well, it didn't work with mine).

There is a patch available that adds some configuration option in the GNOME sound applet, but I have no idea how to apply it. Does anyone know ? (The patch is available at [http://bugzilla.gnome.org/show_bug.cgi?id=173035#c36](http://bugzilla.gnome.org/show_bug.cgi?id=173035#c36))

---

### Post by RSL on 2007-03-06
If any of you are thinking of making the just to Feisty for this, it's worth it. I made the upgrade two days ago and haven't seen a single glitch in the OS so far. [Knock wood.] The keyboard mute and volume controls are working perfectly as well! Woo to the hoo!

---

### Post by gendou on 2007-03-17
It was working for me when it was installed in first place but then stop working when i change the order of the sound cards, and like someone said the girlfriend like the multimedia keys!!!!
i'll try to fix it and post again!!!

---

### Post by wilberfan on 2007-03-19
I've just installed Feisty twice in the last 2 days (don't ask)--and I'm pretty sure that this worked correctly during the first install --but does NOT work now after the 2nd (clean) install!  

:confused: 

I look forward to a solution!   It's a pain to have to grab the mouse and click to lower the volume...!

---

### Post by jimbopouliot on 2007-03-19
It won't necessarily work with Feisty anymore than it worked in Edgy. The difference is, in Feisty, you can now select what sound card and what channel to control using the keyboard media keys.

To do so, go to System.. Preferences.. Sound. There is now something called Default Mixer Tracks. This is what you want to configure. Select your device and track (or tracks) and you should be good to go.

And, by the way, this is a minor detail but still pretty nice: When you want to control the volume using the mouse and the speaker icon in the tray, you don't have to point, click, wait for the slider to show up, slide it and then click elsewhere to make it disappear. You can simply position you cursor on the speaker and then use the mouse wheel directly, without clicking. Pretty nice isn't it ?

Good luck.

---

### Post by wilberfan on 2007-03-27
For what it's worth, this is now working correctly (for me) in Feisty!

:)

---

### Post by trux on 2008-05-02
In Gnome, the volume up/volume down hotkeys (the 'multimedia keys') control the Default Mixer Track. You probably changed its value inadvertently to point to your microphone or other track instead of your main speaker. To modify it back:

1) run gnome-sound-properties (System->Preferences->Sound).
2) change the "Default Mixer Track" option to your soundcard/device and track of your choice (e.g. Master speaker output instead of Capture/Microphone input).

Everything should go back to normal

---

### Post by isecore on 2008-05-02
> **trux said:**
> In Gnome, the volume up/volume down hotkeys (the 'multimedia keys') control the Default Mixer Track. You probably changed its value inadvertently to point to your microphone or other track instead of your main speaker. To modify it back:

1) run gnome-sound-properties (System->Preferences->Sound).
2) change the "Default Mixer Track" option to your soundcard/device and track of your choice (e.g. Master speaker output instead of Capture/Microphone input).

Everything should go back to normal

Just so you know, you're replying to a thread that's more than a year old. Whatever was the issue has surely been corrected by now.

---

