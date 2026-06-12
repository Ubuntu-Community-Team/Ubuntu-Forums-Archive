---
title: "[ Solved ] How to play CBT nuggets Video in Ubuntu 9.10 ??"
date: 2010-02-12
forum: Multimedia Software
---

### Post by thyag on 2010-02-12
How to make ubuntu play CBT nuggets videos:

1. sudo apt-get install mplayer
2. sudo wget [http://www.medibuntu.org/sources.list.d/jaunty.list](http://www.medibuntu.org/sources.list.d/jaunty.list) 
3. document=/etc/apt/sources.list.d/medibuntu.list
4. sudo apt-get install medibuntu-keyring
5. sudo apt-get update
Just execute these once, I really donno y did that but it just worked for me
[http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

6. sudo apt-get install w32codecs libdvdcss2
7. sudo apt-get install mozilla-mplayer
8. sudo apt-get install smplayer
9. Download the codecs zip folder from player to support wmv "http://www.mplayerhq.hu/MPlayer/releases/codecs/" get "win32codecs-essential-20040703.tar.bz2 "
10 Extra it and create a folder "/usr/lib/codecs" and copy the extract .dll file and give exe permission
11 Now copy the CBT codec from "http://www.dlldump.com/download-dll-files_new.php/dllfiles/W/wmsdmod.dll/9.00.00.32508/download.html" get wmsdmod.dll.
12 Copy that your /usr/lib/codecs directory


Thats et all set now u can play CBT nuggets video on Ubuntu using Mplayer !!

-Thyag

********************************************************************
Important Links:
[http://www.dlldump.com/download-dll-files_new.php/dllfiles/W/wmsdmod.dll/9.00.00.32508/download.html](http://www.dlldump.com/download-dll-files_new.php/dllfiles/W/wmsdmod.dll/9.00.00.32508/download.html) : Download the wmsdmod.dll codec from this link
[http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update
********************************************************************
Some keywords for Google to better refine the users search and hit this thread

ubuntu karmic koala 9.10 cbt nuggets video codec wmv how to play

---

### Post by reed1 on 2010-11-09
I did 1 to 6, and then install mplayer then wow, all works ! thanks

---

### Post by sivakumar on 2010-12-04
Guys,

Thanks for the tip.  I'm now able to play  the CBT Files using Firefox Browser.  However I'm facing some issues like, I'm not able to pause / play once it starts.  

Just curious to know if it is possible to see the navigation bar as well.  So that I can fast forward / rewind the video and even pause / play the video.

I'm using Ubuntu 10.10 (Maverick) Edition.

Thanks in advance.

Siva.

---

### Post by wconstantine on 2011-03-05
How to convert CBT Nuggets videos .wmv videos to playable .avi.

Install mencoder.
```
sudo apt-get install mencoder
```

Download and install Binary Codec Packages.
```
wget http://www.mplayerhq.hu/MPlayer/releases/codecs/essential-20071007.tar.bz2
tar -jxvf essential-20071007.tar.bz2
cd essential-20071007
sudo mkdir /usr/lib/codecs
sudo cp * /usr/lib/codecs
cd ..
rm -rf essential-20071007
```

Place the cbt_nugget_convert.sh script in the directory you keep your CBT Nugget videos. 

Give the script executable privileges and then run it.
```
chmod u+x cbt_nugget_convert.sh
./cbt_nugget_convert.sh
```

[COLOR="Red"]**NB! The script will search for all files ending with .wmv and then convert any .wmv files to .avi. It will delete a .wmv file after it has been converted!**[/COLOR]

---

### Post by Le Omar on 2011-06-24
Hi guys; Thanks for the effort its really amazing what you shared, I am having the same problem but i got stuck at second step.. its seems the link [http://www.medibuntu.org/sources.list.d/jaunty.list](http://www.medibuntu.org/sources.list.d/jaunty.list)  is not valid no more valid .. it gives the following message:

**Not Found**

 The requested URL /sources.list.d/jaunty.list was not found on this server.


 .. are there any alternatives? 


Thanks;

---

### Post by beew on 2011-06-25
> **Le Omar said:**
> Hi guys; Thanks for the effort its really amazing what you shared, I am having the same problem but i got stuck at second step.. its seems the link [http://www.medibuntu.org/sources.list.d/jaunty.list](http://www.medibuntu.org/sources.list.d/jaunty.list)  is not valid no more valid .. it gives the following message:

**Not Found**

 The requested URL /sources.list.d/jaunty.list was not found on this server.


 .. are there any alternatives? 


Thanks;

Yes, update your OS. Ubuntu 9.10 has been dead for 2 months, it is no longer supported and the repositories for it are closed down, that's why they aren't  found.

Check the date of OP.

---

### Post by Le Omar on 2011-06-25
Thanks beew; i am actually running ubuntu 11.04 which is the latest and still having the problem .. sorry for not mentioning that earlier.

---

### Post by sumith_p on 2011-07-02
Thanks..wconstantine....
i did it in d same way u told...
but i am getting this when entered the final command....


find: paths must precede expression: ccent02.wmv
Usage: find [-H] [-L] [-P] [-Olevel] [-D help|tree|search|stat|rates|opt|exec] [path...] [expression]...


help me...
i am using ubuntu 11.04 64 bit...

---

### Post by sumith_p on 2011-07-02
Thanks thyag..
i couldnt convert it into avi..so i tried using smplayer to play the .wmv files...but the particular link [http://www.medibuntu.org/sources.list.d/jaunty.list](http://www.medibuntu.org/sources.list.d/jaunty.list)

That link doesnt exist...i have done all the other things possible...
Still i am getting audio only.....
help...
i am using ubuntu 11.04 64 bit...

---

### Post by Le Omar on 2011-08-18
Hi all :)
I found a Jaunty.list link which I used in the steps before instead of the other link, and it worked :) ..
Here it is:
[http://web.mit.edu/source/debathena/scripts/build-server/sources.list.d/ubuntu/jaunty.list](http://web.mit.edu/source/debathena/scripts/build-server/sources.list.d/ubuntu/jaunty.list)

Now I can play videos but not the same way in Windows, I have to go to each video and play it, for HTML I used Epiphany browser, it displays the page but with no video list in it.

the current result is great, i donno if it can be any better.

---

