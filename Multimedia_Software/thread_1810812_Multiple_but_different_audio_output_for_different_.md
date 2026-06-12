---
title: "Multiple but different audio output for different devices"
date: 2011-07-23
forum: Multimedia Software
---

### Post by makcbe on 2011-07-23
Hello there,
I am using Ubuntu 10.04 LTS - the Lucid Lynx. I am using the laptop to play video files and view it on TV using HDMI output. No problems. Requirement: to play _simultaneously_ a _different_ media file and be able to listen through say headphone / laptop speakers. While a movie audio is only heard on TV, other audio is heard only on laptop speaker. Many thanks guys. 
Regards

---

### Post by PPN13 on 2011-07-24
pavucontrol allows you to set different output devices per application (they have to be running to appear on it. I've successfully used it to have skype on my usb headset while keeping all other apps on default speakers. :) 

You might need to install it via 
```
sudo apt-get install pavucontrol
```

---

### Post by makcbe on 2011-07-24
Thanks. I have this installed - could you pl let me know the configuration options if I have to have an HDMI and headphone with different audio outputs?

---

### Post by PPN13 on 2011-07-24
Well I presume you have two different audio devices. One tha outputs through your speakers and your headset jack and one that outputs through your HDMI port (probably part of your graphic card). 

If you run pavucontrol, in the first tab you can select where each running application outputs its sound. I have attached a screenshot with the option highlighted.

---

### Post by makcbe on 2011-07-24
> **PPN13 said:**
> Well I presume you have two different audio devices. One tha outputs through your speakers and your headset jack and one that outputs through your HDMI port (probably part of your graphic card). 

If you run pavucontrol, in the first tab you can select where each running application outputs its sound. I have attached a screenshot with the option highlighted.

Thanks. I have attached the screenshot of pavucontrol. Multiple input devices but both output are only HDMI. :confused:

---

### Post by PPN13 on 2011-07-25
These are not devices on your screenshots but applications (programs). If you click on "Simultaneous output to Internal Audio Digital Stereo" you can change it.Your speakers/headset would probably be an analog device. 

 I have a question though, when you play something on the TV does it also play via the laptop's speakers? Cause it says "Simultaneous"... 

 If you are still having problems perhaps you should post a screenshot of the "Output Devices" tab of pavucontrol.

---

### Post by makcbe on 2011-07-25
> **PPN13 said:**
> These are not devices on your screenshots but applications (programs). If you click on "Simultaneous output to Internal Audio Digital Stereo" you can change it.Your speakers/headset would probably be an analog device. 

 I have a question though, when you play something on the TV does it also play via the laptop's speakers? Cause it says "Simultaneous"... 

 If you are still having problems perhaps you should post a screenshot of the "Output Devices" tab of pavucontrol.
Thanks. I have attached the screenshot of output tab. Though it says simultaneous, no the audio is not played via laptop speakers when it is played thru TV. In fact the TV plays both audio streams same time. What is required is two audio streams - one in laptop speaker and other on TV. I have connected the HDMI cable.

---

### Post by PPN13 on 2011-07-27
> **makcbe said:**
> Thanks. I have attached the screenshot of output tab. Though it says simultaneous, no the audio is not played via laptop speakers when it is played thru TV. In fact the TV plays both audio streams same time. What is required is two audio streams - one in laptop speaker and other on TV. I have connected the HDMI cable.

OK if I understand correctly **"Internal Audio Digital Stereo (HDMI)"** plays only to you laptop's speakers/headphone jack and **"Simultaneous output to Internal Audio Digital Stereo (HDMI)"** plays it only to your tv set. 

 I suppose you want one application to output to tv (say a movie or something) and all rest sounds on laptop.

 So select the **"Internal Audio Digital Stereo (HDMI)"** as default output device in sound preferences from ubuntu's top panel. This should cause all sounds to come from laptop. Then close that window.

 Start the application you want to output to the tv. It will start playing on laptop for now. Pause playback and open *pavucontrol*. Switch to the *playback* tab, find the application and click on its button (see my 1st screenshot) and select **"Simultaneous output to Internal Audio Digital Stereo (HDMI)"**.

  Resume playback and that application (and that only) should be playing through the tv with everything else on the laptop.

  If i guessed wrong regarding which sound device outputs where, or you want all sounds on tv and one application on laptop simply make the opposite choices in ubuntus sound preferences and pavucontrol's playback menu.

Hope it is understandable.

---

