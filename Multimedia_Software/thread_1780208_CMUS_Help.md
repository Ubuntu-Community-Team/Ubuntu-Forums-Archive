---
title: "CMUS Help"
date: 2011-06-11
forum: Multimedia Software
---

### Post by naveenrv87 on 2011-06-11
Hi,

I'm new to CMUS, the terminal-based music player. I had installed it successfully and it seemed to play music perfectly on my headphones.. but ever since i restarted the computer with the headphones unplugged, it doesn't seem to play any music. The error that i see is "Error Selecting output plugin : no such output plugin" . I can see that the output_plugin is blank by default. What can i enter as the value for output_plugin, so that it will play music on both headphones and speaker without errors? And is there a way to find out where my default output plugin is located?

Thanks in advance.

---

### Post by VolatileMember on 2011-06-13
Hello!

do you have installed the latest version of cmus (2.4.1)? It should select the default output plugin far better than the old versions (2.3.x). You can install it using this ppa:
```
sudo add-apt-repository ppa:jmuc/cmus
sudo apt-get update
sudo apt-get install cmus cmus-plugin-ffmpeg
```To see valid output_plugin options, try: ```
cmus --plugins
``` (under "Output Plugins:"). The best choice for a modern Ubuntu system is "pulse".

Does this solve your problem?

---

### Post by VolatileMember on 2011-07-12
Maybe you want to have a look at this thread:
[http://ubuntuforums.org/showthread.php?t=1793090](http://ubuntuforums.org/showthread.php?t=1793090)

(User with similar problem)

---

