---
title: "Skype upgrade Ubuntu 9.10"
date: 2010-01-21
forum: Multimedia Software
---

### Post by dln9 on 2010-01-21
I am running Ubuntu 9.10.  

Today the Update Manager indicated that there was an update available for Skype.  But, in the middle of the installation, I get an error message.  Here is the output:  

(Reading database ... 274767 files and directories currently installed.)
Preparing to replace skype 2.1.0.47-0medibuntu2 (using .../skype_2.1.0.81-1_i386.deb) ...
Unpacking replacement skype ...
dpkg: error processing /var/cache/apt/archives/skype_2.1.0.81-1_i386.deb (--unpack):
 trying to overwrite '/usr/share/icons/skype.png', which is also in package skype-common 0:2.1.0.47-0medibuntu2
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/skype_2.1.0.81-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


I don't understand what the problem is, nor what I should do next.  Please help.  Thanks.

---

### Post by meho_r on 2010-01-21
Try removing the old skype and then install the new one.

---

### Post by dln9 on 2010-01-21
Thanks.  

I tried what you said, but then I could not get the webcam to work.  So, I went back to the skype-common and skype packages for Karmic from the Medibuntu repository, and everything works fine.  

Just for giggles, I did try using the new package that the Update Manager proposed to me after first installing the skype-common package from Medibuntu, but that did not work either.  

It seems the packages offered by Medibuntu are more reliable than those offered via the Update Manager.  Seems crazy to me.

---

### Post by meho_r on 2010-01-25
This (webcam problem) is a known issue. Take a look [here](https://developer.skype.com/LinuxSkype).
> 
Skype does not work well with newer version of GSPCA Webcams driver (Linux Kernel >=2.6.27), possible workaround: 
Ubuntu 32 bit: install "libv4l-0" package and launch Skype with: LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype 
Ubuntu 64 bit: install "lib32v4l-0" package and launch Skype with: LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype 
Other distributions might have the same library, but may have a different path.

To make webcam to work, you should use suggested workaround:

1. Rename **skype** to **skype.real**:
```
sudo mv /usr/bin/skype /usr/bin/skype.real
```

2. Create a new **skype** file in /usr/bin:
```
gksudo gedit /usr/bin/skype
```
Now, enter the following in the file:
```
#!/bin/sh 

LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so  /usr/bin/skype.real "$@"

```

3. Save the file and make it executable:
```
sudo chmod +x /usr/bin/skype
```

Now, restart skype and try your webcam. If it still doesn't work, you may need to restart you computer (however stupid it sounds) and try again.

---

### Post by Puck7 on 2010-01-25
Is the skype in the repos the updated Skype 2.1 Beta 2?

---

### Post by meho_r on 2010-01-25
I don't know which repo OP was using, since I'm not sure it's in official repos at all. I'm using the one from skype webpage.

---

### Post by Puck7 on 2010-01-25
Yes, that's what I wanted to suggest, but I wanted to make sure 1st.

You can download the latest skype from their official website. Link: [http://www.skype.com/intl/en/download/skype/linux/](http://www.skype.com/intl/en/download/skype/linux/)

---

