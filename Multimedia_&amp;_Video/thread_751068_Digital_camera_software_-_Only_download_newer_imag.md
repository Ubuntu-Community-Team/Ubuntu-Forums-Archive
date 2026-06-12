---
title: "Digital camera software - Only download newer images"
date: 2008-04-10
forum: Multimedia &amp; Video
---

### Post by David_H on 2008-04-10
Hi everyone,

I made the decision to go Ubuntu on my laptop a few weeks ago. I have to say I'm overjoyed with the result, The last time I used Linux regularly was 2 years ago while doing my degree and the change in desktop appearance is amazing.

Anyway, to the point. I have a Canon digital camera which I can download the photos from no problem. I tend to use the card reader built in to my laptop and just do it that way. The problem I have been having is downloading only new photos. I have tried both F-Spot and gThumb, but I'm not too keen as they want to rename files and organise the photos in all kinds of complicated ways.

All I want is something to look at the photos on the card, look at them in my particular photos directory, and copy any newer photos over to my hard drive. I'm sure something like this must exist. If not I suppose I could make some bash script but I'd be surprised nobody has wanted this kind of feature before.

Any help much appreciated,
Cheers,
Dave

---

### Post by scorp123 on 2008-04-10
Hmmm ... maybe Google's **Picasa** is for you?
[http://picasa.google.com/](http://picasa.google.com/)

To get Google software for Linux via Synaptic:

1. Open a terminal and copy & paste these lines one by one and execute them:
```
sudo su -
wget --no-check-certificate -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add -
exit

``` .. When it asks for a password: That would most likely be your own password, just type it in blindly (nothing is echoed back!)

2. Execute this command:
```
gksu gedit /etc/apt/sources.list
``` ... A pop-up might ask again for a password. Same as above, it's most likely your own password. Here however you should get some echoes back, e.g. large dots that indicate that the system is receiving the password you're typing (no need to type blindly).

3. The **/etc/apt/sources.list** file should be open and in front of you ... just use the cursor keys to go to the very bottom of the file and then add these lines (copy & paste!):
```
# Google Software
# Key Info: http://www.google.com/linuxrepositories/aboutkey.html
# wget --no-check-certificate -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | apt-key add - 
deb http://dl.google.com/linux/deb/ stable non-free
```

4, Save and close the file

5. Execute these commands:
```
sudo apt-get update
sudo apt-get install picasa
```

Now you should have Picasa on your system .... And there should now be an icon in the "Graphics" menu.

If it's still not what you wanted you can easily get rid of it again:
```
sudo apt-get remove picasa
```

---

### Post by David_H on 2008-04-10
Thanks for your quick reply!

I just had a play round with Picasa and again there are many more features than I'm really looking for. I quite like just browsing my photos in Nautilus and then editing with the Gimp, I just want some way of easily saving new photos from my camera/memory card on to the directory where I have all my photos saved on my hard drive.

Maybe a bash script is the way forward..

Cheers,
Dave

---

### Post by scorp123 on 2008-04-10
> **David_H said:**
>  Maybe a bash script is the way forward.. That would actually be quite easy :)

I will assume that you still use your card reader and e.g. read your SD card containing the photos directly as if it were a floppy disk? So you should get an icon on your desktop everytime you insert your SD card into your system, right?

Can you check where exactly it mounts the card and in which sub-directory (if any) the photos are located?

Example ... I have a HP PhotoSmart 927 digital camera. So when I insert its SD card into my card reader I get a new icon on my desktop:  **HP_927**

A quick check with the **mount** shell command shows that this is the location the card gets mounted to:  **/media/HP_927**

A quick check of that location shows me that all my photos are stored inside a sub-directory, so the complete path to the photos would be:
**/media/HP_927/DCIM/100HP927/**

Can you please check these few things and how they look like in your case?

**_Now, here is the easy part which will do what you want:_**

Let's suppose I just want to insert my card and then hit an icon that auto-syncs the pictures and only grabs the newest ones and then places these new photos into my "Pictures" folder inside my home directory  ...  Here we go:

1. Open a text editor ... e.g. "Text Editor" from the "Accessories" menu will perfectly do

2. Insert these lines:
```
#! /bin/bash 
rsync -av /media/HP_927/DCIM/100HP927/* ~/Pictures/ 
```
( ... obviously the directories above need to be adjusted to the values you need ...)

3. Save the file, name it e.g. **photosync.sh**

4. Make it executable: Open a terminal and then issue this command:
```
chmod 755 photosync.sh
```

5. Insert your SD card and test it inside the terminal:
```
./photosync.sh
``` ... the command should download all the pictures from your SD card.

6. Unmount the SD card (e.g. right-click on its icon and then select "Unmount volume") and take another picture.

7. Insert the card again and repeat step Nr. 5 ... This time only the newest picture (the one you just shot!) should be downloaded!

8. Once we're sure that this part works let's make a launcher icon on the desktop:
[LIST]
[*]right-click on the desktop
[*]Choose the "Select Launcher ..." option
[*]in the pop-up fill in the details: e.g. "PhotoSync" as name, "/home/yourusername/photosync.sh" as command, "sync the photos from the SD card with my Pictures folder" as comment
[*]Click on the "No Icon" button and select a suitable icon ... there should be plenty of icons in the /usr/share/icons folder and subsequent sub-directories there!
[*]That's it ... hit the OK button
[*]Voila, done ... You should have this new program icon on your desktop which will auto-sync your photos when you click on it (no need to open the terminal anymore).
[/LIST]

I hope this is what you wanted and that this posting helped? :)

---

### Post by David_H on 2008-04-18
Hi Scorp,

Just to let you know, I had a play around with the bash scripts and got it all working.  Thanks for your very helpful post. However, I realised the way my camera organises the photos (as I should think is true for most) is all of them in one directory. I really wanted the photos in directories for each day.

I'm very picky I know. Anyway, I have reverted to using F-Spot, and am starting to get used to it. I've read that there should be a duplicates removal feature coming soon, so until then I suppose I'm going to have to try and be careful when importing.

Thanks very much,
Dave

---

