---
title: "sony walkman NWZ A-728B -&gt; ubuntu linux"
date: 2009-10-26
forum: Multimedia Software
---

### Post by bezolaam on 2009-10-26
hello.
I connected my sony walkman to pc (ubuntu 8.04)
and it works fine with amarok,
but the problem is that this model must work  as usb flash device also,
but it doesn't appear on desktop or under computer:///   
so, how to make my device explorable as usb/flash/hdd device?
thanks for   advice

p.s. it worked perfect under windows xp

---

### Post by bezolaam on 2009-10-26
sorry, I have ubuntu 9.04, not 8.04 :)

---

### Post by AmsterdamMack on 2009-10-26
Hi bezolaam,

like CD's, USB drives are showing up under > /mediaHope that was what you've been looking for.

Mack

I found this helpful: [http://www.ubuntugeek.com/linux-or-ubuntu-directory-structure.html](http://www.ubuntugeek.com/linux-or-ubuntu-directory-structure.html)

---

### Post by bezolaam on 2009-10-26
ok, here is sollution I found by googling:
1) sudo gedit /usr/share/hal/fdi/preprobe/10osvendor/20-libgphoto2.fdi
2) I find the string "NWZ-A728b" 
3) I have commented with <!-- and --> the code
<!--
   <match key="usb.vendor_id" int="1356">
    <match key="usb.product_id" int="860">
     <merge key="info.category" type="string">portable_audio_player</merge>
     <append key="info.capabilities" type="strlist">portable_audio_player</append>
     <merge key="portable_audio_player.access_method" type="string">user</merge>
     <merge key="portable_audio_player.type" type="string">mtp</merge>
     <append key="portable_audio_player.output_formats" type="strlist">audio/mpeg</append>
     <merge key="camera.libgphoto2.name" type="string">Sony Walkman NWZ-A728B</merge>
     <merge key="camera.libgphoto2.support" type="bool">true</merge>
    </match>
   </match>
-->
4) Save the file and close

5) restart PC



BUT, when I open my device whit amarok it stops working as USB drive. Then I have to turn off amarok + reconnect device.
 hope its usefull for somebody

---

### Post by 3rdalbum on 2009-10-28
That's a good solution; I used to just "killall gvfs-gphoto2-volume-manager" after mounting the Walkman, then unplug it, then plug it back in.

The new X-series Walkmans work out-of-the-box without such fiddling; maybe take a look at them? :-D  (my old Walkman has gone to my mother)

---

