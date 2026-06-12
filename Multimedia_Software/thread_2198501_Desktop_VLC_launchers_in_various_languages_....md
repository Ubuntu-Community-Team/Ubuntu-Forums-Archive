---
title: "Desktop VLC launchers in various languages ..."
date: 2014-01-09
forum: Multimedia Software
---

### Post by shantiq on 2014-01-09
Trying to set up Desktop VLC launchers in various languages ...

VLC does not allow users to change default language from GUI [which is an odd decision since users of a given machine might need to do that];   it automatically picks the locale language


Thanx to this [thread]("http://ubuntuforums.org/showthread.php?t=1708481")

i saw there is an easy terminal way


so i run

```
LANGUAGE=pt_BR  vlc
```

and

```
LANGUAGE=ru vlc
```   and all is fine


Now my question is   how do i write this in a launcher ?

It works from terminal but not from the launcher in this form


what do i need to write there?


> [Desktop Entry]Encoding=UTF-8
Type=Application
Name=vlc
Name[pt_BR]=vlc
Exec=[COLOR=#000080]LANGUAGE=pt_BR vlc[/COLOR]   ?? [COLOR=#800000][not accepted][/COLOR]   i tried speech marks around command and still no good it probably needs something else   also tried LANGUAGE=pt_BR /usr/bin/vlc

---

### Post by mc4man on 2014-01-09
Whether it works or not you'll need to try (never used anything but my locale
```
Exec=env LANGUAGE=pt_BR  vlc %U
```

Other options would be to create  a small script that launches vlc as desired,  then use in launcher -  (assumes script is in a bin in PATH
```
Exec=scriptname
```
(if you can run the script from alt+f2 then it will always work in ^

..........not really relevant, but will leave..........

Or an bash alias using an export, ex. below of  structure from  one I use
```
alias mplayer1='export VDPAU_DRIVER=va_gl && mplayer'
```
(can go in ~/.bash_aliases

---

### Post by shantiq on 2014-01-09
Thank you Mc 

```
Exec=env LANGUAGE=pt_BR  vlc %U
```


works a dream!



[[IMG]http://img62.imageshack.us/img62/7774/0v1u.th.png[/IMG]]("http://img62.imageshack.us/img62/7774/0v1u.png")


Now i can have 3 VLCs or more in different languages on my desktop depending on mood ::]]

---

### Post by mc4man on 2014-01-09
env usually works well in a .desktop 

Opps - see you don't need below, ...

Here I like to keep the menu in vlc. 14.04 has a gsetting for that now but it doesn't work for qt4 apps so use
```
Exec=env QT_X11_NO_NATIVE_MENUBAR=1  vlc %U
```
If you wanted that you could try 
```
Exec=env QT_X11_NO_NATIVE_MENUBAR=1 LANGUAGE=pt_BR  vlc %U
```

---

### Post by shantiq on 2014-01-09
yes it works too...    earlier one is faster it seems

---

### Post by mc4man on 2014-01-09
Does anything change if reveresed
```
Exec=env LANGUAGE=pt_BR QT_X11_NO_NATIVE_MENUBAR=1 vlc %U
```

---

### Post by shantiq on 2014-01-09
then it is fast again::]]

---

### Post by mc4man on 2014-01-09
> **shantiq said:**
> then it is fast again::]]
Cool, it's good to know that if stringing multi env's the order can matter.

---

