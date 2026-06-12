---
title: "PS3 Eye camera microphone not working"
date: 2012-02-18
forum: Multimedia Software
---

### Post by PaulBZA on 2012-02-18
Hi guys,

I have a problem. I have a webcem (PS3 Eye) and the video works perfectly. With Skype, and all video applications I've tested.

But the microphone doesn't want to work. I have gone into  sound  settings, and checked my input devices, but there is nothing there. They  input devices is grayed out.

Is there any way to get this up and running?

I'm running Ubuntu 11.04, alongside Windows 7.

Thanks.

---

### Post by winh8r on 2012-02-18
Please have a look here for a possible solution.
[http://ubuntuforums.org/showthread.php?t=1785840&highlight=PS3+Eye]("http://ubuntuforums.org/showthread.php?t=1785840&highlight=PS3+Eye")

Hope this helps you.


(posting multiple requests in different sections will not get the answer any quicker than a search of the forum!!!)

Good Luck

---

### Post by Jose Catre-Vandis on 2012-02-18
This also might help (but for PS2 eyetoy)

[http://bimma.me.uk/2011/01/09/ps2-eyetoy-webcam-on-xubuntu-1010-recording-and-playback/](http://bimma.me.uk/2011/01/09/ps2-eyetoy-webcam-on-xubuntu-1010-recording-and-playback/)

---

### Post by PaulBZA on 2012-02-18
> **winh8r said:**
> Please have a look here for a possible solution.
[http://ubuntuforums.org/showthread.php?t=1785840&highlight=PS3+Eye](http://ubuntuforums.org/showthread.php?t=1785840&highlight=PS3+Eye)

Hope this helps you.


(posting multiple requests in different sections will not get the answer any quicker than a search of the forum!!!)

Good Luck

Thanks, I'm going to try your suggestion first, and see how it works. I'm feeling confident about it working. However, I'm a noob at Ubuntu and the poster said to solve he had to add a line to the "00main" file in the "Init" directory. However, I it only opens the file as read only, and even saving it to the desktop, I can't copy and paste it to replace the one I already have and I'm hopeless when it comes to  commands in the terminal to replace it.

So how can I replace the existing 00main file?

---

### Post by winh8r on 2012-02-18
You can edit the read-only file by entering in the terminal:


```
sudo gedit /path/to/filename
```


edit what you need to and then click on save.

Use this with care though, as read only files are set that way for a reason, to prevent them being written to. However when you do need to alter them then this is one way to do it.

---

### Post by PaulBZA on 2012-02-19
OK guys, I tried that  method there, but with no luck. I replaced the 00main file by logging as root, and replaceing the file. But one restart later still nothing. Really hope to get this working, so I can move onto new experiments.

---

### Post by tuppe666 on 2012-05-27
Try trying this.

pacmd load-module module-alsa-source device=hw:1,0

then do this

sudo echo "load-module module-alsa-source device=hw:1,0" >> /etc/pulse/default.pa

From

[http://renatocunha.com/blog/2012/04/playstation-eye-audio-linux](http://renatocunha.com/blog/2012/04/playstation-eye-audio-linux)

---

### Post by Xero Xenith on 2012-07-01
> **tuppe666 said:**
> Try trying this.

pacmd load-module module-alsa-source device=hw:1,0

then do this

sudo echo "load-module module-alsa-source device=hw:1,0" >> /etc/pulse/default.pa

From

[http://renatocunha.com/blog/2012/04/playstation-eye-audio-linux](http://renatocunha.com/blog/2012/04/playstation-eye-audio-linux)

This fixed the problem for me! Many thanks :)

---

### Post by BoogeyOfTheMan on 2012-07-06
> **tuppe666 said:**
> Try trying this.

pacmd load-module module-alsa-source device=hw:1,0

then do this

sudo echo "load-module module-alsa-source device=hw:1,0" >> /etc/pulse/default.pa

From

[http://renatocunha.com/blog/2012/04/playstation-eye-audio-linux](http://renatocunha.com/blog/2012/04/playstation-eye-audio-linux)

Whenever I try that, I get:
boogeyman@boogeyman-desktop:~$ sudo echo "load-module module-alsa-source device=hw:1,0" >> /etc/pulse/default.pa
bash: /etc/pulse/default.pa: Permission denied
boogeyman@boogeyman-desktop:~$ pacmd load-module module-alsa-source device=hw:1,0
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> boogeyman@boogeyman-desktop:~$ 

What am I doing wrong?

---

### Post by mickey12gauge on 2012-07-20
> **BoogeyOfTheMan said:**
> Whenever I try that, I get:
boogeyman@boogeyman-desktop:~$ sudo echo "load-module module-alsa-source device=hw:1,0" >> /etc/pulse/default.pa
bash: /etc/pulse/default.pa: Permission denied
boogeyman@boogeyman-desktop:~$ pacmd load-module module-alsa-source device=hw:1,0
Welcome to PulseAudio! Use "help" for usage information.
>>> >>> boogeyman@boogeyman-desktop:~$ 

What am I doing wrong?

I get the same... 

>>> >>> quenton@quenton-T3612:~$  sudo echo "load-module module-alsa-source devi0" >> /etc/pulse/default.pa
bash: /etc/pulse/default.pa: Permission denied
quenton@quenton-T3612:~$ pacmd load-module module-alsa-source device=hw:1,0
Welcome to PulseAudio! Use "help" for usage information.

A star (*) next to a name means that the command is disabled.

 job_spec [&]                            history [-c] [-d offset] [n] or hist>
 (( expression ))                        if COMMANDS; then COMMANDS; [ elif C>
 . filename [arguments]                  jobs [-lnprs] [jobspec ...] or jobs >
 :                                       kill [-s sigspec | -n signum | -sigs>
 [ arg... ]                              let arg [arg ...]
 [[ expression ]]                        local [option] name[=value] ...
 alias [-p] [name[=value] ... ]          logout [n]
 bg [job_spec ...]                       mapfile [-n count] [-O origin] [-s c>
 bind [-lpvsPVS] [-m keymap] [-f filen>  popd [-n] [+N | -N]
 break [n]                               printf [-v var] format [arguments]
 builtin [shell-builtin [arg ...]]       pushd [-n] [+N | -N | dir]
 caller [expr]                           pwd [-LP]
 case WORD in [PATTERN [| PATTERN]...)>  read [-ers] [-a array] [-d delim] [->
 cd [-L|[-P [-e]]] [dir]                 readarray [-n count] [-O origin] [-s>
 command [-pVv] command [arg ...]        readonly [-aAf] [name[=value] ...] o>
 compgen [-abcdefgjksuv] [-o option]  >  return [n]
 complete [-abcdefgjksuv] [-pr] [-DE] >  select NAME [in WORDS ... ;] do COMM>
 compopt [-o|+o option] [-DE] [name ..>  set [-abefhkmnptuvxBCHP] [-o option->
 continue [n]                            shift [n]
 coproc [NAME] command [redirections]    shopt [-pqsu] [-o] [optname ...]
 declare [-aAfFgilrtux] [-p] [name[=va>  source filename [arguments]
 dirs [-clpv] [+N] [-N]                  suspend [-f]
 disown [-h] [-ar] [jobspec ...]         test [expr]
 echo [-neE] [arg ...]                   time [-p] pipeline
 enable [-a] [-dnps] [-f filename] [na>  times
 eval [arg ...]                          trap [-lp] [[arg] signal_spec ...]
 exec [-cl] [-a name] [command [argume>  true
 exit [n]                                type [-afptP] name [name ...]
 export [-fn] [name[=value] ...] or ex>  typeset [-aAfFgilrtux] [-p] name[=va>
 false                                   ulimit [-SHacdefilmnpqrstuvx] [limit>
 fc [-e ename] [-lnr] [first] [last] o>  umask [-p] [-S] [mode]
 fg [job_spec]                           unalias [-a] name [name ...]
 for NAME [in WORDS ... ] ; do COMMAND>  unset [-f] [-v] [name ...]
 for (( exp1; exp2; exp3 )); do COMMAN>  until COMMANDS; do COMMANDS; done
 function name { COMMANDS ; } or name >  variables - Names and meanings of so>
 getopts optstring name [arg]            wait [id]
 hash [-lr] [-p pathname] [-dt] [name >  while COMMANDS; do COMMANDS; done
 help [-dms] [pattern ...]               { COMMANDS ; }

---

