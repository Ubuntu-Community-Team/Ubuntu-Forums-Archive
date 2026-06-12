---
title: "Chinese Trail Camera Wont Mount, Neither will Memcard."
date: 2020-07-03
forum: Multimedia Software
---

### Post by adambond on 2020-07-03
Im running 64bit Ubuntu 18.04.4 LTS

The camera is a LESHP trail camera. Takes SD cards. You must format the card inside the camera just for it to mount in the camera. Therefore, i have no idea what the card is formatted to. (FAT, NTSC, ..etc)

When i plug the camera, or just the SD card into Ubuntu, there is no mounting. (ive verified all cables and ports work with other memcards and cam components)
When plugged into Ubuntu, the camera powers up properly and the screen shows a usb and says 'MSDC'. 

My XP computer recognized the SD card, but wont open it, says it needs formatted. 

Any suggestions on how to atleast get the card to mount in Ubuntu?


 [ATTACH=CONFIG]286387[/ATTACH]

---

### Post by Autodave on 2020-07-04
I did a little research on your post and about the only thing that I found was that there are a multitude of people who had problems of every kind with that unit.

Are you capable of displaying the images on the trail camera itself?  If not, then I would suspect that the card didn't get formatted properly.

---

### Post by Skaperen on 2020-07-04
sounds to me like the camera uses a proprietary file system on the card.  the 1st command might get the data off of the card.  it could take quite a while to run.  check to see how big the file is (2nd command).
```

bzip2 -9 < /dev/sdb > camcard.img.bz2
ls -l camcard.img.bz2

```

---

### Post by Autodave on 2020-07-04
That's why I asked if they could view the pics on the camera.  If they can, then a proprietary format is most likely the cause.

---

### Post by adambond on 2020-07-05
> **Autodave said:**
> I did a little research on your post and about the only thing that I found was that there are a multitude of people who had problems of every kind with that unit.

Are you capable of displaying the images on the trail camera itself?  If not, then I would suspect that the card didn't get formatted properly.

Excellent question.  The camera does have a screen and provisions for viewing the files. However I did not, i pulled the card and  put it into my computer.  (when im out in the field, to save battery life, I dont view them on the camera, I pull the card and download, and return the card later.)  

So once I determined I could not mount the card in my comp, i reinstalled it back in the camera. When I turn the cam on, it says "...Memory initialize..."    then  !Card Error!.  And ive tried holding buttons to get to menu and everything about 1000times. So there doesnt appear to be any way to load it in the cam itself.... now. :(  

A side note, when I first got the camera, I put the sd card in my laptop and formated to FAT like I do with all my other trail cams. That way i can just slip the sd card in the cam and go. Well, not this camera. It did not like it, and wanted to format it in the camera. So that is how I go it to accept the sd card and take pics. And I know it took pics. Atleast I seen it operating when the deer were passing through. 

I'll gladly post the pics here if i can get the darn things off there. 

I will try the suggestions and report back. Thanks a bunch!

---

### Post by adambond on 2020-07-05
No dice. [ATTACH=CONFIG]286398[/ATTACH]

---

### Post by Autodave on 2020-07-05
I would try another known good card.  Let the camera format it,  Take a oic and then see if you can view it.  If so, then we can figure out what it is formatted to.  I believe that you either have a bad card or a defective camera.

---

### Post by adambond on 2020-07-12
Ok. I got it to format a smaller card. It renamed that card 'SD-FAT16' .   

I took a video with it. It is in AVI format.

---

### Post by Autodave on 2020-07-13
Good deal!  Please remember to mark this thread as "Solved".

---

### Post by adambond on 2020-07-13
No. I still have that same problem. That first memory card that I cant get to mount in anything. 

I was just posting my results. Not sure what to do with them, or how to tell what this 2nd card it formatted to.  Im assuming FAT16. ?  And not sure what that means in terms of getting the other card to cooperate.

---

### Post by CelticWarrior on 2020-07-13
Depending on age the camera may not support cards bigger than 2GB, the original SD standard. That won't be the case if a bigger card (SDHC or SDXC) formats and work in the camera itself. If this is what's happening - not sure, your whole thread is confusing - then it's a case of a proprietary format that only works in the camera, as already commented.

---

### Post by tea for one on 2020-07-13
> **adambond said:**
> No. I still have that same problem. That first memory card that I cant get to mount in anything. 

I was just posting my results. Not sure what to do with them, or how to tell what this 2nd card it formatted to.  Im assuming FAT16. ?  And not sure what that means in terms of getting the other card to cooperate.

Ubuntu will recognise FAT16 file system, why not pop the card into your PC and enter in the terminal

```
sudo parted -l
```

You may see something like this

```
Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1967MB  1966MB  primary  fat16
```

When you have established that your PC can recognise FAT16, then you can reformat the un-coperative card.

---

### Post by Autodave on 2020-07-13
Let me get this straight becuase I am confused now.  The second card works in the camera and you can play the video back in the camera?  But the card isn't recognized in Linux?  If so, then it has some weird proprietary format.

If that is so, then the first card was formatted to the camera and nothing is going to read it but the camera.  If the first card doesn't even work in the camera, then it sounds like a bad card.

Correct me if I have this wrong.

---

### Post by adambond on 2020-07-14
I am currently running an identical 32gb card in that camera with no problems. 

To  reiterate, the issue is, i installed a 32gb card into the cam. It asked  me to format it. I did.  The next day, removed the card to install in  pc. No mount. So reinstalled in camera, it rejects it also.  I have  several other cards that work fine in the cam now. Including one  identical to the problem card. 

> **tea for one said:**
> Ubuntu will recognise FAT16 file system, why not pop the card into your PC and enter in the terminal

```
sudo parted -l
```

You may see something like this

```
Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1967MB  1966MB  primary  fat16
```

When you have established that your PC can recognise FAT16, then you can reformat the un-coperative card.


Alright, with the buggy 32gb card in, this is the response I get. 
[ATTACH=CONFIG]286463[/ATTACH]

---

### Post by tea for one on 2020-07-14
I was expecting you to display the result of a working SD card - not the misbehaving card, which does not have a partition table.

Can you remove all external drives/devices from your PC, pop in the known working SD card and run ```
sudo parted -l
``` from the terminal.

Please post the results within code tags because it is easier to read.

---

