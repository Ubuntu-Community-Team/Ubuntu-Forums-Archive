---
title: "Question about Skype"
date: 2009-12-03
forum: Multimedia Software
---

### Post by dln9 on 2009-12-03
I am using Ubuntu 9.10, and Skype 2.1.  I can successfully connect with other people via Skype.  But, while I can see and hear them, they cannot see nor hear me.  

In Skype when I do the audio test, it works fine.  When I go to the option to test my video, I cannot see anything.  Clicking on the button to test the video results in nothing happening that I can tell - not even an error message.  

Please help, we would like to communicate with our daughter in college.  Thanks.

---

### Post by meho_r on 2009-12-03
For camera, you may try these:

1. Move **/usr/bin/skype** to **/usr/bin/skype.real**. You can do this with this command:
```
sudo mv /usr/bin/skype /usr/bin/skype.real
```

2. Install **lib32v4l-0**:
```
sudo apt-get install lib32v4l-0
```

3 Create a new **/usr/bin/skype**:
```
sudo gedit /usr/bin/skype
```

4. After gedit opens, paste these lines and save the document:
```

#!/bin/bash
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype.real

```

5. You may have to make skype file you just created executable:
```
sudo chmod +x /usr/bin/skype
```

6. Run skype as usual.

BTW, did you test your camera in any other application (e.g. emesene or cheese)? Does it work?

---

### Post by dln9 on 2009-12-03
Hey, thanks.  

Yes, the camera works just fine in Cheese.  

I tried your suggestion.  No change.  In options, if I try the test, nothing happens.  When I call someone, and select the option to show myself on my video during the call, all I see is a grey box.

---

### Post by meho_r on 2009-12-03
Try logout or restart with camera turned on.

---

### Post by dln9 on 2009-12-03
How do I do that?  I am not aware of any on/off button on the camera.

---

### Post by meho_r on 2009-12-03
Just keep it plugged in :) Sorry for confusion. I tested on my Logitech camera: after doing above steps, I still had black screen (but I plugged the camera in USB after doing them). After logout it worked.

---

### Post by saltmore on 2009-12-04
Here is my script to launch skype. You have yours working but only way could get my cam to work. May be useful for others.

#!/bin/sh
export XLIB_SKIP_ARGB_VISUALS=1
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
exit 0

---

### Post by dln9 on 2009-12-04
meho_r:  I never unplug my camera, so, Yes, evertime I shutdown and then startup the computer I am doing what you suggest (if I'm understanding you correctly).  

saltmore:  I am not familiar with "scripts".  What exactly would I do with the code (?) you posted?  Do I go to the terminal and type it in exactly as you showed?

---

### Post by meho_r on 2009-12-04
Well, if that code didn't work for you, then you may take a look [here.](http://ubuntuforums.org/showthread.php?p=8307588)

EDIT: I've just installed skype from [Medibuntu](https://help.ubuntu.com/community/Medibuntu) repository and it works without any hacking. You may give it a try.

---

### Post by dln9 on 2009-12-04
Thanks.  I uninstalled Skype, and then reinstalled it, but this time from the Medibuntu repository, and it works perfectly.

---

