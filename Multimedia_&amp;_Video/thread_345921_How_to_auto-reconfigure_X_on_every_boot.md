---
title: "How to auto-reconfigure X on every boot?"
date: 2007-01-24
forum: Multimedia &amp; Video
---

### Post by stuporglue on 2007-01-24
Note: I am NOT looking for "sudo dpkg-reconfigure xserver-xorg". I know what that does and it's good, but not in this situation. :-) 

I have Ubuntu installed on an external USB HD (see [this post]("http://ubuntuforums.org/showthread.php?p=2011285")). I am currently using the following dpkg command in my gdm startup script to auto-reconfigure the Xorg.conf file on each restart of the X server with no interaction.

```
dpkg-reconfigure -fnoninteractive --no-reload -phigh xserver-xorg
``` 

On lots of computers, this works just wonderfully. On a few systems though, it doesn't work. On these same systems the Ubuntu 6.10 live CD auto detects the video options correctly. 

Does anyone know how the live CD does its video detection? Or, a better way to auto reconfigure Xorg.conf on each boot? 

My USB disk is something of a traveler and regularly boots on several different machines. I'm also the TA for ~35 students with similar USB disk setups, and it'd be nice to find a better solution than the command we're using.

Thanks, 
Michael

---

