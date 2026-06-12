---
title: "iPod Touch + Videos?!"
date: 2010-06-04
forum: Multimedia Software
---

### Post by SubOneForty on 2010-06-04
hey all, ive been trying numerous programs to get .mp4 tv shows onto my iPod touch to no avail. :( is there a simple solution i have missed??

---

### Post by clintec on 2010-06-04
I think we are all in the same boat.

We are currently tracking this in the following thread:
[URL="http://ubuntuforums.org/showthread.php?t=1481506"]
http://ubuntuforums.org/showthread.php?t=1481506[/URL]

I hope we can get this figured out soon.

Thanks,
clintec.

---

### Post by aa4bb on 2010-06-05
Here's a solution I'm using:

Get GoodReader from the App Store. You can  set up folders in GoodReader just as you would on your computer. You  can mount it in Nautilus over WiFi and transfer files to and from its  file system just like a remote drive. Once those files are there, if  they are a file type recognized by GoodReader, and including videos  (!!), it will open and display / play them!!!

Here's how: Start the GoodReader app. The left-most icon in the task bar  at the bottom takes you to a page "WiFi-transfer". If you have  connected your iPod to your WiFi, this page will show "WiFi status: ON"  and "Connection: not established". It will also show "IP address:  http://192.168.1.104:8080" or something similar. 

Now in Ubuntu, start Nautilus, choose File>Connect to Server...
Under "Service Type", choose "WebDAV (HTTP)". In "Server", enter IP  address  (192.168.1.104, for example) and in "Port" enter 8080, as found  on the GoodReader display. Click "Connect". Another instance of  Nautilus pops up, showing the GoodReader's file system. On the iPod,  Connection now changes to "established".

Just drag and drop, copy and paste, or whatever, and it works like you  think it should. Transfers are very fast!! 

Once you have the files copied over, unmount the iPod and tap Done on  the WiFi Transfer page of GoodReader. Then navigate the file system and  tap on the file to play. If it's a video, it starts playing.

This is not ideal, and there may be a limit on total size of the  GoodReader directory, but it's better than nuttin'.

---

