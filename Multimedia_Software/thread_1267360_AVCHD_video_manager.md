---
title: "AVCHD video manager"
date: 2009-09-15
forum: Multimedia Software
---

### Post by syncmasterpt on 2009-09-15
Hi!

I have a Canon HF200 that produces AVCHD files, and I'm also an 100% Linux [Kubuntu] user. 

For playing this files I use WDTV connected to my TV, and on Linux VLC does play them more or less OK. Some jitter, but it's watch-able.

The main issue is how to manage all my AVCHD media... Photos, is easy because Picasa, gphoto, digikam, the do a nice job, but for avchd media there is no comparable software.

Because files are copied directly from the camera SD card to the computer, files have names like 000045.MTS, and so on, and with a lot of them, it's starting hard to manage all this video.

So my question is: 

 Is there any software that allows to:

 Scan for avchd media, allows to rename the file, tags them, shows thumbnails or litle previews?

 Basically Picasa for AVCHD files :)

Thanks!

---

### Post by zingo on 2010-02-14
I also have trouble to get the AVCHD files from my camera in an automatic script. How do other solve this?

I used a script that use gphoto2 for camera downloads basically it does
```

DIR=$BACKUP_ROOT/`date +%F`
cd $DIR
gphoto2 --port=usb --get-all-files --filename 20%y%m%d_%H%M%S_%04n.%C

```

But for my new camera a Panasonic DMC-TZ7 it seems that gphoto2 don't even list the avchdlite (avchd) movie files at all only the images.

/PRIVATE/AVCHD/BDMV/STREAM in the camera contains 3  .MTS AVCHDlite files

```
zingo@dual:~/tmp/slask$ ls -la /media/NO_NAME/PRIVATE/AVCHD/BDMV/STREAM
totalt 166656
drwx------ 2 zingo zingo    32768 2009-01-01 00:00 .
drwx------ 5 zingo zingo    32768 2009-01-01 00:00 ..
-rwxr-xr-x 1 zingo zingo 23930880 2010-02-14 13:23 00000.MTS
-rwxr-xr-x 1 zingo zingo 66490368 2010-02-14 15:08 00001.MTS
-rwxr-xr-x 1 zingo zingo 80099328 2010-02-14 16:39 00002.MTS

```

but gphoto2 cant find them. 
In disk mode (usbmasstorage mode or PC mode on the camera) I get

```
zingo@dual:~/tmp/slask$ gphoto2 --port=disk: -L -R
There is no file in folder '/'.                                                
There is no file in folder '/DCIM'.                                            
There are 3 files in folder '/DCIM/100_PANA'.                                  
#1     P1000050.JPG               rd   118 KB image/jpeg
#2     P1000050.MOV               rd 190048 KB video/quicktime
#3     P1000051.JPG               rd  3861 KB image/jpeg
There is no file in folder '/MISC'.                                            
There is no file in folder '/PRIVATE'.                                         
There is no file in folder '/PRIVATE/AVCHD'.                                   
There is no file in folder '/PRIVATE/AVCHD/AVCHDTN'.                           
There is no file in folder '/PRIVATE/AVCHD/BDMV'.                              
There is no file in folder '/PRIVATE/AVCHD/BDMV/CLIPINF'.                      
There is no file in folder '/PRIVATE/AVCHD/BDMV/PLAYLIST'.                     
There is no file in folder '/PRIVATE/AVCHD/BDMV/STREAM'.                       
There is no file in folder '/PRIVATE/AVCHD/IISVPL'. 

```

In PTP mode (Pictbridge mode on the camera) I get

```
zingo@dual:~/tmp/slask$ gphoto2 --port=usb: -L -R
There is no file in folder '/'.                                                
There is no file in folder '/store_00010001'.                                  
There is no file in folder '/store_00010001/DCIM'.
There is 1 file in folder '/store_00010001/DCIM/100_PANA'.
#1     P1000051.JPG               rd  3861 KB 3072x2304 image/jpeg
There are 2 files in folder '/store_00010001/DCIM/100_PANA/46190032'.
#2     P1000050.JPG               rd   118 KB 1280x720  image/jpeg
#3     P1000050.MOV               rd 190048 KB video/quicktime
There is no file in folder '/store_00010001/MISC'.
```

---

