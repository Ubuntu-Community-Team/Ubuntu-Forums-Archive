---
title: "MPlayer Parse error at line 4"
date: 2015-11-27
forum: Multimedia Software
---

### Post by DiRe on 2015-11-27
Hello,I installed the mplayer but when i tried to use occured one error:

dire@DiRe-PC-Linux:~/Desktop$ mplayer
parse error at line 4

other example of error:

dire@DiRe-PC-Linux:~/Desktop$ mplayer teste.mp3 
parse error at line 4 

Can help me??
Regards, DiRe

---

### Post by bodyeuh on 2015-11-27
please install vlc instead. type in terminal : sudo apt-get install vlc

---

### Post by blm-ubunet on 2015-11-27
mplayer has a ascii text config file.
The error could be junk in this file.
~/.mplayer/config

Depending on your distro version..
You might like to checkout a later version (& loads of other good stuff) from this ppa:-
[https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media](https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media)

---

### Post by andrew.46 on 2015-11-27
To see the error in the config file try:

```

cat ~/.mplayer/config

```

and post the output here. To see just the first few lines:

```

cat ~/.mplayer/config | head -n 5

```

Another option is to avoid using the config file at all and start mplayer with:

```

mplayer -noconfig all teste.mp3

```

Several options available for -noconfig to allow testing of exactly where the issue is:


```

 -noconfig <options>
       Do not parse selected configuration files.
       NOTE: If -include or -use-filedir-conf options are specified  at  the  command
       line, they will be honoured.

       Available options are:
         all
               all configuration files
         gui (GUI only)
              GUI configuration file
         system
              system configuration file
         user
              user configuration file

```

---

### Post by Rob Sayer on 2015-11-28
> **bodyeuh said:**
> please install vlc instead. type in terminal : sudo apt-get install vlc

Some people prefer mplayer, and with reason.

---

### Post by DiRe on 2015-12-01
Hi,

with this option mplayer work:

> [COLOR=#000000][FONT=Ubuntu Mono]mplayer -noconfig all teste.mp3 [/FONT][/COLOR]

the result of cat is:

> # Write your default config options here!



&#8220;nolirc=yes&#8221;

what i need to change to work only "mplayer teste.mp3"??

Thanks

---

### Post by andrew.46 on 2015-12-01
Instead of :

```
“nolirc=yes” 
```

try 

```
nolirc=yes
```

and this might be enough...

---

### Post by DiRe on 2015-12-02
thank you, this work....

---

### Post by andrew.46 on 2015-12-02
> **DiRe said:**
> thank you, this work....

Great news, I hope you continue to enjoy MPlayer! I think the tides have turned a little against it but it is certainly still my preferred player...

---

