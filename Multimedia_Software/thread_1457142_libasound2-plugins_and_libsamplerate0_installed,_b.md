---
title: "libasound2-plugins and libsamplerate0 installed, but files missing?"
date: 2010-04-18
forum: Multimedia Software
---

### Post by BrabusDay5 on 2010-04-18
Hello,

I am trying to make the sound quality better on my Ubuntu. I have read some tips in this topic: [http://ubuntuforums.org/archive/index.php/t-766114.html](http://ubuntuforums.org/archive/index.php/t-766114.html). This made to go to this topic: [http://ubuntuforums.org/showpost.php?p=4793993&postcount=9 ]("http://ubuntuforums.org/showpost.php?p=4793993&postcount=9")
It says there this: (If you are lazy to click ;))
 				 				[B]

Re: NEED better audio quality[/B] 			
 			 			 		   		 		 		 	Quote:
 	 	 		 			 				 					Originally Posted by **ztheory** 					[[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=4790705#post4790705") 				
 				*I can tell you flat out that foobar with the secret rabbit plugin, even without any internal or external equalizer completely tears up linux sound.*
 			 		 	 	 
No, it doesn't.

In Linux you can easily choose Secret Rabbit in SRC_SINC_BEST_QUALITY mode as your system-wide sample rate converter by adding a single line to either /etc/asound.conf or ~/.asoundrc (requires libasound2-plugins and libsamplerate0 to be installed):
 	Code:
 	defaults.pcm.rate_converter "samplerate_best" 
Now show me how to do that in Windows.




Now i need help. I have both of those packages installed, but for some reason the file asound.conf and .asoundrc are not there so I cannot add the line. Any help? 
Thanks

---

### Post by Yellow Pasque on 2010-04-18
I didn't have one either. You could create the file like this:
```
gksu gedit /etc/asound.conf
```
However, I think the hack you're referring to is outdated. It probably controls ALSA's software mixer, dmix, which has been replaced by pulseaudio.

To change the resampling of pulseaudio:
```
gksu gedit /etc/pulse/daemon.conf
```
Change this line:
```
resample-method = speex-float-1
```
to:
```
resample-method = src-sinc-best-quality
```
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by WinterRain on 2010-04-18
```
gksu gedit /etc/asound.conf
```
will not create a new .conf file. you need to:
```
sudo touch /etc/asound.conf
```
to make a new one.

---

### Post by Yellow Pasque on 2010-04-18
> **WinterRain said:**
> ```
gksu gedit /etc/asound.conf
```
will not create a new .conf file.
Sure it will (as long as you modify the blank file and save it before exiting).

---

