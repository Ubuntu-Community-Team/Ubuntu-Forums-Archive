---
title: "Guide me to setup up M-Audio Fast Track Pro"
date: 2010-06-23
forum: Multimedia Software
---

### Post by jonasbdotcom on 2010-06-23
Hello,

I have seen the vast amount of solutions and guides to set up Fast Track Pro soundcard with Ubuntu, and I simply cannot get any of them to work. Right now I'm using Traktor LE in Windows using the Fast Track Pro with Vestax VCI-100.

I wish to have the M-Audio Fast Track Pro to work with all four channels - but right now I can only get 2 channels working. I have seen the guide to compile a new kernel - but that only works for Ubuntu 8 i guess.

Can anyone help me with setting up the device with four channes using Ubuntu 10.04 which I use. 

Thanks. :KS

---

### Post by cchhrriiss121212 on 2010-06-23
So what do you want to do with this on Ubuntu, audio production or just playback? In which case are you using jack? This device is supported and I've seen plenty of users on here with functioning output, so you shouldn't need to compile any kernels. I'm not sure about the Vestax compatibility, how is it connected?

From an [old thread]("http://ubuntuforums.org/showthread.php?t=1474468&highlight=fast+track+pro") on the studio forum, showing how to get jack working:
> you need to specifically indicate a subdevice for this device in order to get any inputs. So for the input device you need to enter hw:1,1 and for the output device just hw:1

---

### Post by jonasbdotcom on 2010-06-23
Thanks for you quick reply...

Well, the setup is that I wish to be able to que the tunes in my monitor ch1+ch2 (in this case my headphones) and have the actual playback in ch3+ch4. I tried installing JACK - but I guess it's difficult to set up.

However, I have read that there should be some issues with the Vestac VCI-100 and ubuntu.

---

