---
title: "ssh and remote x errors"
date: 2009-10-03
forum: Networking &amp; Wireless
---

### Post by mbuell on 2009-10-03
I log in to my remote server via ssh, and then I can run gui apps. When I do, error messages show up in the terminal session. Can anybody tell me what they mean?

Please note particularly:
Xlib:  extension "Generic Event Extension" missing on display "localhost:10.0".

** (gnome-system-monitor:14047): WARNING **: SELinux was found but is not enabled.

If you read the excerpt below, you will also see that I tried to resolve this using the export command - which actually seemed to eph things up. I can get gedit and the system monitor to run without it. 

```
hiero@debian:~$ xhost +168.192.0.4
168.192.0.4 being added to access control list
hiero@debian:~$ ssh -X hiero@168.192.0.4
hiero@168.192.0.4's password: 
Linux hiero-ubuntu 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:49:34 UTC 2009 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/

0 packages can be updated.
0 updates are security updates.

Last login: Sat Oct  3 15:03:24 2009 from 168.192.0.5
hiero@hiero-ubuntu:~$ gedit
Xlib:  extension "Generic Event Extension" missing on display "localhost:10.0".
Xlib:  extension "Generic Event Extension" missing on display "localhost:10.0".
Xlib:  extension "Generic Event Extension" missing on display "localhost:10.0".
Xlib:  extension "Generic Event Extension" missing on display "localhost:10.0".
Xlib:  extension "Generic Event Extension" missing on display "localhost:10.0".
Xlib:  extension "Generic Event Extension" missing on display "localhost:10.0".
hiero@hiero-ubuntu:~$ export DISPLAY=168.192.05:10.0
hiero@hiero-ubuntu:~$ gedit

(gedit:12147): Gtk-WARNING **: cannot open display: 168.192.05:10.0
hiero@hiero-ubuntu:~$ export DISPLAY=168.192.05
hiero@hiero-ubuntu:~$ gedit

(gedit:12175): Gtk-WARNING **: cannot open display: 168.192.05
hiero@hiero-ubuntu:~$ export --help
-bash: export: --: invalid option
export: usage: export [-nf] [name[=value] ...] or export -p
hiero@hiero-ubuntu:~$ man export
No manual entry for export
hiero@hiero-ubuntu:~$ export DISPLAY=168.192.05 -n
-bash: export: `-n': not a valid identifier
hiero@hiero-ubuntu:~$ export -n DISPLAY=168.192.05 
hiero@hiero-ubuntu:~$ export
declare -x HISTCONTROL="ignoreboth"
declare -x HOME="/home/hiero"
declare -x LANG="en_US.UTF-8"
declare -x LESSCLOSE="/usr/bin/lesspipe %s %s"
declare -x LESSOPEN="| /usr/bin/lesspipe %s"
declare -x LOGNAME="hiero"
declare -x LS_COLORS="no=00:fi=00:di=01;34:ln=01;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.svgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.lzma=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.rar=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:"
declare -x MAIL="/var/mail/hiero"
declare -x OLDPWD
declare -x PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
declare -x PWD="/home/hiero"
declare -x SHELL="/bin/bash"
declare -x SHLVL="1"
declare -x SSH_CLIENT="168.192.0.5 43726 22"
declare -x SSH_CONNECTION="168.192.0.5 43726 168.192.0.4 22"
declare -x SSH_TTY="/dev/pts/0"
declare -x TERM="xterm"
declare -x USER="hiero"
declare -x XDG_SESSION_COOKIE="054e6b6936078992e043208f4a760967-1254602489.435836-1236174790"
hiero@hiero-ubuntu:~$ gnome-system-monitor

(gnome-system-monitor:12678): Gtk-WARNING **: cannot open display: 
hiero@hiero-ubuntu:~$ gedit

(gedit:13571): Gtk-WARNING **: cannot open display: 
hiero@hiero-ubuntu:~$ exit
logout
^[[A

exit
^Chiero@debian:~$ 
hiero@debian:~$ ssh -X hiero@168.192.0.4
hiero@168.192.0.4's password: 
Linux hiero-ubuntu 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:49:34 UTC 2009 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/

0 packages can be updated.
0 updates are security updates.

Last login: Sat Oct  3 16:41:29 2009 from 168.192.0.5
hiero@hiero-ubuntu:~$ gedit
Xlib:  extension "Generic Event Extension" missing on display "localhost:10.0".
Xlib:  extension "Generic Event Extension" missing on display "localhost:10.0".
Xlib:  extension "Generic Event Extension" missing on display "localhost:10.0".
Xlib:  extension "Generic Event Extension" missing on display "localhost:10.0".
Xlib:  extension "Generic Event Extension" missing on display "localhost:10.0".
Xlib:  extension "Generic Event Extension" missing on display "localhost:10.0".
hiero@hiero-ubuntu:~$ gnome-system-monitor
Xlib:  extension "Generic Event Extension" missing on display "localhost:10.0".
Xlib:  extension "Generic Event Extension" missing on display "localhost:10.0".
Xlib:  extension "Generic Event Extension" missing on display "localhost:10.0".
Xlib:  extension "Generic Event Extension" missing on display "localhost:10.0".
Xlib:  extension "Generic Event Extension" missing on display "localhost:10.0".
Xlib:  extension "Generic Event Extension" missing on display "localhost:10.0".

** (gnome-system-monitor:14047): WARNING **: SELinux was found but is not enabled.

Xlib:  extension "Generic Event Extension" missing on display "localhost:10.0".
hiero@hiero-ubuntu:~$
```

Thanks;
Hiero

---

### Post by bkaplan on 2009-11-06
I'm getting the same error ... can anyone explain?

Xlib:  extension "Generic Event Extension" missing on display "localhost:10.0"

I'm running 9.04 on Toshiba Satellite A205-S5855
SSH'ing into remote host computer via:

ssh -Y [email]user@XXX.XXX.XXX.XXX[/email]

Please note that the same error results using -X switch.

Any help would be greatly appreciated!

-Barry

---

### Post by mbuell on 2009-11-06
I've still not figured this one out - but I can work with what I'm getting, so I haven't worried about it.

---

