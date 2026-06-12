---
title: "irexec only working once"
date: 2014-07-06
forum: Mythbuntu
---

### Post by Lester_Burnham on 2014-07-06
Hi,

I have been using irexec for launching the mythbuntu theme for various mythbox's for a long time, but sometimes it will only launch the menu once.
If I exit the menu back to the desktop to do something, then hit my configured remote button to re-launch, nothing happens.

remote is an RC6 clone (works fine)
I use the following files in the users home folder to launch:
~/mythtv_user/.lircrc
```
#Custom lircrc generated via mythbuntu-lirc-generator
#All application specific lircrc files are within ~/.lirc
include ~/.lirc/mythtv 
include ~/.lirc/mplayer 
include ~/.lirc/xine 
include ~/.lirc/vlc 
include ~/.lirc/xmame 
include ~/.lirc/xmess 
include ~/.lirc/totem 
include ~/.lirc/elisa
include ~/.lirc/irexec
```

~/mythtv_user/.lirc/irexec
```
begin
     prog = irexec
     button = LiveTV
     config = mythfrontend --service
end
```

I have the users exit the menu, to let the box shutdown when not in use. (ACPI wake)
The thing that confuses me, is that 9/10 boxes work fine and are able to re-launch, but the odd one out is a one shot affair.

Am I using irexec in the correct manner?

The current system is a mythbuntu 14.04 with 0.27 fixes on an i3
Would I be better off setting these up using the mythtv user, if it will let me.
I normally just create an xbmc user, that is added to the mythtv group.

Any help appreciated.
Thanks,
Lester

ps: If anyone has a good mythshutdowncheck script, that also checks for mythweb access, that would be greatly appreciated :)

---

### Post by khPWXxF on 2014-07-14
Forgive me if I'm missing the point completely but my 12.04 system isn’t like that.  This is how I get a power button on my TV remote to force myth frontend back to the welcome screen:

 
/etc/lirc/lircd.conf has includes to files like this:
 
```

include "/usr/share/lirc/remotes/mceusb/lircd.conf.mceusb"
include "/usr/share/lirc/remotes/samsung/lircd.conf.samsungUE32F5500"

```
That second file in turn tells lirc about lengths of IR pulses etc and which patterns of 1s and 0s to look for to interpret (say) me pressing the second power button on my TV controller..
 
Eg
 
```
begin remote

  name      Samsung
  bits           16
 [ … etc … ]
 
      begin codes
          KEY_POWER                0x40BF
          KEY_POWER2               0x07F8

```
 
 
I then have a file saying which program to invoke when I press that button on my TV remote:
 
/home/phil/.mythtv/lircrc is a link to  /home/phil/.lirc/mythtv

This has entries like:
 
```
begin
    remote = Samsung
    prog = irexec
    button = KEY_POWER2
    config = /usr/bin/remotepower.sh
    repeat = 0
    delay = 0
end

```
 
I note that:

[LIST=1]
[*]You don’t have a ‘remote’ line to say which remote it should look for,
[*]I’m suspicious of your use of the ~ in your includes.  It may well be fine, but /home/user might be safer.  Not sure that lirc runs under 'your user' anyway.
[*]there is a mismatch between your ‘include’ directives and the filename you quote, though it might just be a typing error.
[/LIST]
 
To diagnose further I think I'd trigger a script to simply 
```
date>>/home/phil/my.log
``` 

Hope this helps.
Phil

---

