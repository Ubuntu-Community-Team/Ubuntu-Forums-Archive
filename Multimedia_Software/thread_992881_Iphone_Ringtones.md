---
title: "Iphone Ringtones"
date: 2008-11-25
forum: Multimedia Software
---

### Post by memo-pima on 2008-11-25
Hi everybody,

I spend last night finding a way make ringtones for my Iphone out of my own MP3s. I managed to write a script to do it for me and it seems it's working, so there my little contribution to community.

What you need :
-pacpl (the perl audio converter)
-mp3splt (to cut the mp3 to the right lenght)
-mp3info (to get tag of the mp3 so you can rename the file juste with the name of the track)
-sftp
-faac
-a jailbroken Iphone with OpenSSH

```

#!/bin/bash

folder=/home/memo/.temp/
title=$(mp3info -p %t "$1")


cd $folder

#Cut the MP3 to the first 40 second
mp3splt "$1" 0.0 0.40 -o temp

#convert to m4a
pacpl --to m4a temp.mp3

#change the extension to m4r and rename the file withe the title of the track
mv temp.m4a "$title.m4r"

#connect to the iphone via ssh and copy the ringtone
sftp root@<the name of your Iphone>.local<<EOF
cd  "/Library/Ringtones"
put "$folder$title.m4r"
EOF

#remove all temp file
rm  temp.mp3
rm "$title.m4r"
```

It will ask for a password which is "alpine" by default on the iphone 3G. If someone got any advice for a passwordless connection... I didn't try yet. Then you just have to make it a nautilus script. I suggest however to run it in a terminal before to check if it's working properly.

Voila ! My first script ever, so any feedback is more than welcome.

---

### Post by wmoore on 2008-12-27
Thanks for this - this is something I have been trying (and failing miserably) to do. Having said that, I keep getting errors. When I run the script, I get the following message (truncated):
> Converting:  [temp.mp3] -> [m4a] encode failed with exit status: 256
 The key line is the 'encode failed with exit status: 256'. If I run 'paclpl -v --to m4a JumpAround.mp3', I get this (again truncated):
> ffmpeg: unrecognized option '--title'
encode failed with exit status: 256I disected the deb package and looked at the pacpl binary for --title. Most of the instances were related to KDE error message popups but I found the following line that I thought may be *the one*:
> switch ($type) {
        case /mp4|m4a|m4b/ { return "**--title** \"$tag_name{title}\" --track \" ....
But changing this to -title or title didn't remove the error message.

Any chance you could help me out here?

Cheers.

---

### Post by memo-pima on 2008-12-30
Hey,


Sorry for my late answer. 
Try installing faac, and it should be fine.
Sorry for forgetting to put this one on the list of required package.

Tell me if it's still not working.

By the way I find the way to make a passwordless connection.

First you should follow this link :[Copying files with scp and sftp]("http://www.bo.infn.it/alice/alice-doc/mll-doc/linux/admin/node54.html") (the sftp part)


If it's still not working, then follow this (which is a part of this [howto]("https://help.ubuntu.com/community/PortableDevices/iPhone"))

#SSH to your iphone : 

> ssh root@<iphone name>

# Edit /etc/sshd_config or /etc/ssh/sshd_config:

      > nano /etc/ssh/sshd_config

# Scroll down to the segment beginning with '#RSAAuthentication', and set it up as follows:
> 
      RSAAuthentication yes
      PubkeyAuthentication yes
      AuthorizedKeysFile .ssh/authorized_keys

      Remove any commenting hashmarks (#) prepended to the beginning of these three lines. 

# Hit Ctrl+X to exit, and save your changes.
# At this point you should be finished. Reboot your device.

      > reboot

Then, hopefully, you would able to transfer ringtone from mp3 to your iphone with a simple right click and without password.

---

### Post by memo-pima on 2008-12-30
Now it looks likw I am having some issues with mp3info and ID3 V2.

I am gonna look into that and update this soon.

---

### Post by wmoore on 2008-12-30
> **memo-pima said:**
> Hey,


Sorry for my late answer. 
Try installing faac, and it should be fine.
Sorry for forgetting to put this one on the list of required package.
Sweet as! Works like a charm now (except for the one track I pick that had a '/' in the tags).

---

### Post by memo-pima on 2008-12-30
there is the script for nautilus that will work with ID3v2 and ID3v1 using pacpl. So no need of mp3info anymore.

> 
#!/bin/bash

echo "$1"
#try to extract the Title out of the ID3V2 tag.
title=$(pacpl --taginfo "$1" |grep "Title" |sed 's/  Title: //g')

#Cut the MP3 to the first 40 second
mp3splt "$1" 0.0 0.40 -o temp


#convert to m4a
pacpl --to m4a temp.mp3


#change the extension to m4r and rename the file withe the title of the track
mv temp.m4a "$title.m4r"


#connect to the iphone via ssh and copy the ringtone
sftp [email]root@<name of your iPhone>.local[/email]<<EOF
cd  "/Library/Ringtones"
put "$title.m4r"
EOF

#remove all temp file
rm  temp.mp3
rm "$title.m4r"


---

### Post by memo-pima on 2009-06-26
None of those work for linux... no idea why this is here...


After losing on my iphone for some stupid reason, I had to put my ringtone again, but having reinstalled my laptop and completly and forgot about this script I had to find it again. I made just a little improvement for the transfer via ssh. After the script there all the instruction to make it work.

```
#!/bin/bash
#any issues, email me at Godin.guillaume@gmail.com

#try to extract the Title out of the ID3V2 tag.
title=$(pacpl --taginfo "$1" |grep "Title" |sed 's/ Title: //g')

#Cut the MP3 to the first 40 second
mp3splt "$1" 0.0 0.40 -o temp


#convert to m4a
pacpl --to m4a temp.mp3


#change the extension to m4r and rename the file withe the title of the track
mv temp.m4a $title.m4r


#connect to the iphone via ssh and copy the ringtone
scp $title.m4r root@[COLOR="Red"]<name of your iphone>[/COLOR].local:/Library/Ringtones/

#remove all temp file
rm temp.mp3
rm "$title.m4r" 
```

Instruction :

Make sure all this package are install :

-pacpl
-mp3splt
-faac

Then you need a jailbroken Iphone into which you can SSH (you can find instruction for that on the ubuntu website).

Then put this script in /home/your user name/.gnome2/nautilus-script/ folder, replace the red bit by your iphone name, make it executable :
$ chmod +x <your script>

Connect your iphone to the wifi. Open nautilus, right click on the song you wnat to transfer and select script then the script itself. It might ask for a password (that is alpine, unless you changed it).

If everything went fine, you should now have a new ringtone with the first 40 second of your favorite mp3.

Enjoy

---

### Post by TDFZ on 2010-04-15
Another easy way.

Sound Converter can convert an MP3 to an m4a.  Just look in sound converters preferences.   After converting the mp3 rename the .m4a to .m4r,  ssh on to iPhone and place the file in the Ringtones folder.

---

