---
title: "runvdr script issue"
date: 2006-11-28
forum: Multimedia &amp; Video
---

### Post by Kako on 2006-11-28
Hi Guys,

I have an issue with a script that is supposed to start VDR (I'm on Edgy Eft)
Here is the script:

```
#!/bin/sh
#
# Script de lancement de VDR
#
test -f /etc/sysconfig/vdr && . /etc/sysconfig/vdr
if [ ! $? -eq 0 ]
then
	echo "Il vous manque le fichier de configuration /etc/sysconfig/vdr"
	exit 2
fi

VDRCMD="$VDRPRG -w 0 -L $VDRLIBPATH -s $VDRPATH/vdrshutdown -c $VDRCONF  -v $VDRVIDEO/records $* \
                -P "pluginsetup" -l 3"

export DVDCSS_METHOD=key
KILL="/usr/bin/killall -q -TERM"

while (true) do
      ALL_PLUGINS=`cat $VDRCONF/plugins/plugin_setup_runvdr.conf`
echo $VDRCMD $ALL_PLUGINS
      $VDRCMD $ALL_PLUGINS
#      su $VDRUSR -c "$VDRCMD $ALL_PLUGINS"
      if test $? -eq 0 -o $? -eq 2; then exit; fi
      date
      echo "Red&#65533;marrage de VDR"
      $KILL $VDRPRG
      sleep 10
      date
      done
```

And the /etc/sysconfig/vdr file:

```
export VDRPATH=/usr/local/bin
export VDRLIBPATH=/usr/local/lib/vdr
export VDRPRG=$VDRPATH/vdr
export VDRVIDEO=/video
export VDRCONF=$VDRVIDEO/vdrconf
export VDRLOG=/var/log/vdr.log
export VDRUSR=root
export LANG=C
export LC_ALL=C
export LC_CTYPE=C
```

When I try to start VDR using this script, here is the output I get:
```
kako@mediaplayer:~$ sudo runvdrlog
Password:
/usr/local/bin/vdr -w 0 -L /usr/local/lib/vdr -s /usr/local/bin/vdrshutdown -c /video/vdrconf -v /video/records -P pluginsetup -l 3 -P "launcher" -P "ac3mode" -P "epgsearch" -P "extrecmenu" -P "femon" -P "nordlichtsepg" -P "otv4vdr" -P "otvepg" -P "osdpip" -P "osdteletext -d /tmp/vtx" -P "pilotskin" -P "pin" -P "prefermenu" -P "reelchannelscan" -P "rotor" -P "setup" -P "skinsoppalusikka -l /video/vdrconf/plugins/logos" -P "span" -P "streamdev-server" -P "streamdev-client" -P "sysinfo" -P "subtitles" -P "text2skin" -P "timeline" -P "trayopen" -P "tvonscreen -l /video/vdrconf/plugins/logos" -P "vod" -P "vompserver" -P "xine" -P "yaepg" -P "remote -i /dev/input/event2"
vdr: missing plugin '"launcher"'
vdr: missing plugin '"ac3mode"'
vdr: missing plugin '"epgsearch"'
vdr: missing plugin '"extrecmenu"'
vdr: missing plugin '"femon"'
vdr: missing plugin '"nordlichtsepg"'
vdr: missing plugin '"otv4vdr"'
vdr: missing plugin '"otvepg"'
vdr: missing plugin '"osdpip"'
vdr: missing plugin '"osdteletext'
vdr: missing plugin '"pilotskin"'
vdr: missing plugin '"pin"'
vdr: missing plugin '"prefermenu"'
vdr: missing plugin '"reelchannelscan"'
vdr: missing plugin '"rotor"'
vdr: missing plugin '"setup"'
vdr: missing plugin '"skinsoppalusikka'
vdr: invalid log level: /video/vdrconf/plugins/logos"
kako@mediaplayer:~$
```

Of course, I have already checked that all required plugins are actually installed in /usr/local/lib/vdr.

However, if I type the command line manually (output of echo $VDRCMD $ALL_PLUGINS in runvdr script), then VDR starts correctly !!!

```
kako@mediaplayer:~$ sudo -i
root@mediaplayer:~# . /etc/sysconfig/vdr
root@mediaplayer:~# /usr/local/bin/vdr -w 0 -L /usr/local/lib/vdr -s /usr/local/bin/vdrshutdown -c /video/vdrconf -v /video/records -P pluginsetup -l 3 -P "launcher" -P "ac3mode" -P "epgsearch" -P "extrecmenu" -P "femon" -P "nordlichtsepg" -P "otv4vdr" -P "otvepg" -P "osdpip" -P "osdteletext -d /tmp/vtx" -P "pilotskin" -P "pin" -P "prefermenu" -P "reelchannelscan" -P "rotor" -P "setup" -P "skinsoppalusikka -l /video/vdrconf/plugins/logos" -P "span" -P "streamdev-server" -P "streamdev-client" -P "sysinfo" -P "subtitles" -P "text2skin" -P "timeline" -P "trayopen" -P "tvonscreen -l /video/vdrconf/plugins/logos" -P "vod" -P "vompserver" -P "xine" -P "yaepg" -P "remote -i /dev/input/event2"
-------------------------
MakePrimaryDevice: 1
=========================
SetVideoFormat: 1
frame: (0, 0)-(-1, -1), zoom: (1.00, 1.00)
SetAudioChannelDevice: 0
SetVolumeDevice: 255
SetPlayMode: 1
```

Can someone explain what I'm doing wrong here ? And should I change this to make it working ?

Many many thanks
Kako

---

