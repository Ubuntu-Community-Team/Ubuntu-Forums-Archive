---
title: "Unable to install libavcodec-extra-53 codec"
date: 2014-09-10
forum: Multimedia Software
---

### Post by alfirdaous on 2014-09-10
Hello everybody,

I tried to install the **libavcodec-extra-53** codec, but failed:

```

$ sudo apt-get install libavcodec-extra-53
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libavcodec-extra-53 : Depends: libavutil-extra-51 (< 4:0.8.15ubuntu0.12.04.1-99) but 7:2.3.3-0ppa1~precise is to be installed
E: Unable to correct problems, you have held broken packages.

```

Then I tried **libavutil-extra-51**, which is already installed:

```

aburayane@aburayane:~$ sudo apt-get install libavutil-extra-51
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libavutil-extra-51 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.

```

[IMG]http://s14.postimg.org/4q3jvl8y9/Screenshot_from_2014_09_10_11_26_13.png[/IMG]

Thanks for your help

---

### Post by alfirdaous on 2014-09-10
I deleted the VLC + SimpleScreenRecorder from the synaptic package with their PPA from the folder /etc/apt/sources.list.d, and then installed the codec again, and I installed the SimpleScreenRecorder, finally it works, thanks

---

