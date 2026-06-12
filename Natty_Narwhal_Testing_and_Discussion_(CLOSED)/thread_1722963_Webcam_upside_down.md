---
title: "Webcam upside down"
date: 2011-04-06
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by rlklee on 2011-04-06
My laptop's webcam video output is upside down in Skype (old and recently released versions). 

This is not a new problem and there are a good number of threads which pose the same solution, which up till 11.04 has worked fine.

From the longest most [helpful forum thread]("http://ubuntuforums.org/showthread.php?t=1460790")

```
 WEBCAM: to solve the image upside-down problem, we have to run this command:

sudo add-apt-repository ppa:libv4l/ppa && sudo apt-get update && sudo apt-get upgrade

```

That would solve the problem globally (except for skype) in Ubuntu releases previous to 11.04. In 11.04 no global problem seems to exist (cheese outputs correctly) and *only* seems to exist in Skype. 

Normally the solution would be to create a wrapper to launch Skype

```

#!/bin/sh

if [ ! -e ~/.Skype/shared.xml ]; then
mkdir -p ~/.Skype
cp /usr/share/skype/shared.xml ~/.Skype/shared.xml
fi

LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so QT_PLUGIN_PATH=/usr/lib32/qt4/plugins /usr/bin/skype "$@" 

``` 

But this depends on v4l1compat.so and that normally is provided by the ppa already mentioned above. That ppa no longer provides this in Natty, apparently.  

Does anyone know how I might go about solving this issue?

---

### Post by cariboo on 2011-04-06
Are you using the Maverick version of skype from the partner repositories?

---

### Post by rlklee on 2011-04-06
I am using the 64bit Ubuntu 10.04+ version provided [here]("http://www.skype.com/intl/en/get-skype/on-your-computer/linux/") on Skype's website.

---

### Post by rlklee on 2011-04-06
OK, interesting. I uninstalled the package provided by Skype's website and installed from the maverick partner repo and the video is now working. 

This is fine, but I'm wondering if there are any steps I can take to get the same functionality out of the newer version.

---

### Post by rlklee on 2011-04-06
OK, apparently my idiocy got away from me. Everything is as it should be. The wrapper works, the libv4l compats are supplied by 11.04 w/o any ppa. I'm not sure how I missed them in the first place. 

This works with the Skype in the maverick partner repos and works just as well with the skype supplied from skypes website.

---

