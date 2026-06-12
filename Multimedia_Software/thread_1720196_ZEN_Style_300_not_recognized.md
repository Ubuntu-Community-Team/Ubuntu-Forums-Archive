---
title: "ZEN Style 300 not recognized"
date: 2011-04-03
forum: Multimedia Software
---

### Post by Moamen on 2011-04-03
My Creative ZEN Style 300 player is not recognized in Ubuntu 10.10 through media players (Rhythembox, Banshee, Gnomad2...etc) .
it is recognized correctly as a removable media like any flash drive ,but not as a media player though. 

I've searched a the issue and found some solutions to other Creative ZEN models ,but none worked for me. 

here is my *lsusb* output:
```
Bus 002 Device 006: ID 041e:2016 Creative Technology, Ltd 
```
I've edited the */lib/udev/rules.d/45-libmtp8.rules*
 file and added ```
# Creative ZEN Style 300
ATTR{idVendor}=="041e", ATTR{idProduct}=="2016", SYMLINK+="libmtp-%k", MODE="660", GROUP="audio"
```
and edited the*/usr/share/hal/fdi/information/20thirdparty/20-libmtp8.fdi* file and added :
```
 <!-- Creative ZEN Style 300 -->
      <match key="usb.vendor_id" int="0x041e">
        <match key="usb.product_id" int="0x2016">
          <match key="info.capabilities" contains_not="portable_audio_player">
            <append key="info.capabilities" type="strlist">portable_audio_player</append>
          </match>
          <merge key="info.vendor" type="string">Creative</merge>
          <merge key="info.product" type="string">ZEN Style 300</merge>
          <merge key="info.category" type="string">portable_audio_player</merge>
          <merge key="portable_audio_player.access_method" type="string">user</merge>
          <match key="portable_audio_player.access_method.protocols" contains_not="mtp">
            <append key="portable_audio_player.access_method.protocols" type="strlist">mtp</append>
          </match>
          <append key="portable_audio_player.access_method.drivers" type="strlist">libmtp</append>
          <match key="portable_audio_player.output_formats" contains_not="audio/mpeg">
            <append key="portable_audio_player.output_formats" type="strlist">audio/mpeg</append>
          </match>
          <match key="portable_audio_player.output_formats" contains_not="audio/x-ms-wma">
            <append key="portable_audio_player.output_formats" type="strlist">audio/x-ms-wma</append>
          </match>
          <merge key="portable_audio_player.libmtp.protocol" type="string">mtp</merge>
        </match>
      </match>
``` 
Still no luck though , any suggestions ?

---

### Post by Moamen on 2011-04-03
any help !!

---

### Post by StrayEddy on 2011-07-13
Same problem as you, i think Zen Style devices are not supported by libmtp for now, we should report a request for the new m100 and m300 devices.

For your info, it works great with windows media player (alternative till there is a solution on linux)

Look here: [http://ubuntuforums.org/showthread.php?t=1617280](http://ubuntuforums.org/showthread.php?t=1617280)

---

### Post by StrayEddy on 2011-07-13
Also you could try toZen:

[http://homepages.shu.ac.uk/~cmsps/freeScripts/#toZen]("http://homepages.shu.ac.uk/%7Ecmsps/freeScripts/#toZen")

I didn't try it, at your own risk, but maybe it works great.

---

### Post by StrayEddy on 2011-07-14
You can always just drag and drop ;). Works on linux ;)

---

