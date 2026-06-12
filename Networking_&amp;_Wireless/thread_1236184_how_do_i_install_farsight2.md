---
title: "how do i install farsight2"
date: 2009-08-10
forum: Networking &amp; Wireless
---

### Post by jarrah-95 on 2009-08-10
when i try to install farsight2 for amsn the ./configure fails and the end of the output says
```

checking for PYFARSIGHT... configure: error: Package requirements ( pygobject-2.0 >= 2.12.0 
                                   gst-python-0.10 >= 0.10.10 ) were not met:               

No package 'pygobject-2.0' found
Package pygtk-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `pygtk-2.0.pc'
to the PKG_CONFIG_PATH environment variable                   
Package 'pygtk-2.0', required by 'gst-python', not found      

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.                      

Alternatively, you may set the environment variables PYFARSIGHT_CFLAGS
and PYFARSIGHT_LIBS to avoid the need to call pkg-config.             
See the pkg-config man page for more details.                         

jarrah@jarrah-laptop:~/farsight2-0.0.12$ sudo apt-get install pygobject-2.0
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package pygobject-2.0
jarrah@jarrah-laptop:~/farsight2-0.0.12$ sudo apt-get install pygobject
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package pygobject
jarrah@jarrah-laptop:~/farsight2-0.0.12$ sudo apt-get install pygobject-dev
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package pygobject-dev
jarrah@jarrah-laptop:~/farsight2-0.0.12$

```
how do i fix this to get farsight to work also if it is a package that i need what is the name
thanks

---

### Post by jarrah-95 on 2009-08-10
i have installed some of the needed packages but the rest i cant find. 
this is where im up to now
```

Requested 'pygobject-2.0 >= 2.12.0' but version of PyGObject is 2.6.0
Package pygtk-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `pygtk-2.0.pc'
to the PKG_CONFIG_PATH environment variable
Package 'pygtk-2.0', required by 'gst-python', not found

```
what packages do i need to install
thanks

---

### Post by kevdog on 2009-08-10
Did you try searching for it in the archives:

sudo apt-cache search pygobject

---

### Post by jarrah-95 on 2009-08-11
no but i did try apt-get and and i also serched synaptic and i have installed everything that came up that looked right

---

### Post by Moustaffa on 2009-11-29
I have the exact same problem, isn't there anyone who could help solve this problem? It would be much appreciated

---

### Post by Claus7 on 2009-11-30
Hello,

there is a long time since I was facing problems about the installation of farsight in Dapper. For the pygobject thing, I think that the pygtk-2.12.1.tar.gz might do the trick, yet I do not remember for sure. There have been years since then...

[http://ubuntuforums.org/showpost.php?p=4871922&postcount=4](http://ubuntuforums.org/showpost.php?p=4871922&postcount=4)

Even though I would not like to say such things, I would not advice you to try such procedure in versions less than karmic. If you do try to make the compilation of farsight and afterwards to make it work with amsn, I would most like to see this effort. Have in mind that in karmic is already compiled for you, even if it is not working as it should at the moment.

Regards!

---

### Post by Hilko on 2009-12-01
Same problem here. I really hate to reboot in windows to talk to people on windows live messenger.
I really really hope someone can help and give instructions to get farsight2 installed for amsn. It will be very very very much appreciated.

---

### Post by Hilko on 2009-12-01
Ok i've found this in some (i think) spanish post

[http://ubuntuforums.org/showthread.php?t=1321171](http://ubuntuforums.org/showthread.php?t=1321171)
> **deafters said:**
> Hola, yo uso karmic y para instalar el amsn 0.98 lo que tuve que hacer es desinstalar el que tenia ( busque en synaptic todo lo que fuera amsn y lo desinstale completamente, eliminando toda configuración guardada), luego agregue este repositorio:
deb [http://ppa.launchpad.net/amsn-daily/ppa/ubuntu](http://ppa.launchpad.net/amsn-daily/ppa/ubuntu) karmic main
actualice (sudo apt-get update) y luego instale ( sudo apt-get install amsn) aceptando todos los paquetes sugeridos y listo, 
espero te sirva

Having no idea what is says i just tried this
-completely remove the packages amsn and amsn-data.
-add ```
deb [http://ppa.launchpad.net/amsn-daily/ppa/ubuntu](http://ppa.launchpad.net/amsn-daily/ppa/ubuntu) karmic main
``` to your software sources.
-reload all the packages.
-install amsn and amsn-plugins-extra
I ignored all the warnings about the authentication of the new repository. If you wanna do this is up to you.

It seems promising. I have not actually made a voice or video call yet, but when i started amsn and went into the preferences it said farsight2 was installed and everything looked ok.
I hope it really works.

---

### Post by swissz on 2010-01-09
Hi Hilko!
And how is it? Is it working now?
Regards!

---

### Post by Hilko on 2010-01-10
It does not work like i hoped it would. I have not been able to make a video cal. Audio call worked kind of, but far from perfect. The sound stream was interrupted frequently with blocks of silence. I was able to hear someone at the other end and that one could hear me.
However, i still need to reboot in windows to make a call.

Maybe it can be improved if i configure my devices differently ? I don't know. Has anyone had better results ?

---

### Post by shadchelaka on 2010-03-23
i tried what you did hilko and as you said everything worked out. i can now use amsn 0.98.3. thankx for that

nway i went to preferences n tried to configure my audio/video settings.
once i've done everything this came out:

"Audio/Video call capabilities have been disabled in this version of amsn because M$oft has changed their protocols again and disabled access to their SIP servers, blocking amsn from giving you access to this feature."

hope this helps. cheers.

---

### Post by fonsi2099 on 2010-11-02
:guitar: the same problem for me, thank you for any help!

---

