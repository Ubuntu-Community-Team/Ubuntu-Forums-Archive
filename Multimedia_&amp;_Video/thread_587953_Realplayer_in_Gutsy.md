---
title: "Realplayer in Gutsy?"
date: 2007-10-23
forum: Multimedia &amp; Video
---

### Post by Anicka on 2007-10-23
Is realplayer available for gutsy? I cannot find it in medibuntu. Anyone knows if/when/where it will be?

---

### Post by wieman01 on 2007-10-23
Open the repositories file:
> sudo gedit /etc/apt/sources.list
Add this line:
```
deb http://archive.canonical.com/ubuntu feisty-commercial main
```
Then update:
> sudo apt-get update
And install Realplayer:
> sudo apt-get install realplay

---

### Post by wieman01 on 2007-10-23
Sorry, that was for Feisty... Try this instead:
```
wget -c http://www.debian-multimedia.org/pool/main/r/realplay/realplayer_10.0.9-0.1_i386.deb
```
```
sudo dpkg -i realplayer_10.0.8-0.1_i386.deb
```
This is the reference: [http://www.howtoforge.com/the_perfect_desktop_ubuntu_gutsy_gibbon_p6]("http://www.howtoforge.com/the_perfect_desktop_ubuntu_gutsy_gibbon_p6")

---

### Post by Anicka on 2007-10-23
Thanks I will try it tonight.

---

### Post by nisarg on 2007-10-24
As far as I know if you have apps installed via Synaptic Package Manager or Add/Remove programs they can track their version and update it automatically.
Will installing RealPlayer with this method update automatically? Will it create all the menu shortcuts?

> **wieman01 said:**
> Sorry, that was for Feisty... Try this instead:
```
wget -c http://www.debian-multimedia.org/pool/main/r/realplay/realplayer_10.0.8-0.1_i386.deb
```
```
sudo dpkg -i realplayer_10.0.8-0.1_i386.deb
```
This is the reference: [http://www.howtoforge.com/the_perfect_desktop_ubuntu_gutsy_gibbon_p6]("http://www.howtoforge.com/the_perfect_desktop_ubuntu_gutsy_gibbon_p6")

---

### Post by wieman01 on 2007-10-24
> **nisarg said:**
> As far as I know if you have apps installed via Synaptic Package Manager or Add/Remove programs they can track their version and update it automatically.
Will installing RealPlayer with this method update automatically? Will it create all the menu shortcuts?
No automatic updates, however, the menu entries will be created of course. I prefer the repository solution as well, but I could not find anything like that for Gutsy.

---

### Post by Anicka on 2007-10-24
Thank you wieman! It worked like a charm. Now I can listen to my favourite webradio again.

---

### Post by nisarg on 2007-10-24
Cheers Weiman01. Indeed, installing it via the repository is the best way to go around getting it. Coming from a windows background - I also tend to get concerned when I will need to uninstall realplayer, how was I going to do it without having it show up on S.P.M or Add/Remove programs?
So, whats the issue there?
Is the application not added to the Medibuntu repository by Ubuntu? It seems a little odd that such popular application isnt there on a repository to install on most popular linux desktop.

---

### Post by wieman01 on 2007-10-24
> **nisarg said:**
> Cheers Weiman01. Indeed, installing it via the repository is the best way to go around getting it. Coming from a windows background - I also tend to get concerned when I will need to uninstall realplayer, how was I going to do it without having it show up on S.P.M or Add/Remove programs?
So, whats the issue there?
Is the application not added to the Medibuntu repository by Ubuntu? It seems a little odd that such popular application isnt there on a repository to install on most popular linux desktop.
No idea actually. I did not find it in any of the repositories. Gone with the wind, but tomorrow is another day. :-)

---

### Post by ukripper on 2007-10-24
> **wieman01 said:**
> Open the repositories file:

Add this line:
```
deb http://archive.canonical.com/ubuntu feisty-commercial main
```
Then update:

And install Realplayer:

Isn't this suppose to be Gutsy instead of Feisty?
```
deb http://archive.canonical.com/ubuntu feisty-commercial main
```

```
deb http://archive.canonical.com/ubuntu gutsy-commercial main
```

---

### Post by wieman01 on 2007-10-24
> **ukripper said:**
> Isn't this suppose to be Gutsy instead of Feisty?
```
deb http://archive.canonical.com/ubuntu feisty-commercial main
```

```
deb http://archive.canonical.com/ubuntu gutsy-commercial main
```
It is. I corrected it in my next post. One solution for Feisty, one for Gutsy.

---

### Post by ukripper on 2007-10-24
> **wieman01 said:**
> It is. I corrected it in my next post. One solution for Feisty, one for Gutsy.

Sorry didn't read that!

Cheers

---

### Post by nisarg on 2007-10-24
OK - has anyone tried it to confirm realplayer on gutsy can be installed from 
```
deb http://archive.canonical.com/ubuntu gutsy-commercial main
```
?
Cheers!

> **ukripper said:**
> Isn't this suppose to be Gutsy instead of Feisty?
```
deb http://archive.canonical.com/ubuntu feisty-commercial main
```

```
deb http://archive.canonical.com/ubuntu gutsy-commercial main
```

---

### Post by wieman01 on 2007-10-24
> **nisarg said:**
> OK - has anyone tried it to confirm realplayer on gutsy can be installed from 
```
deb http://archive.canonical.com/ubuntu gutsy-commercial main
```
?
Cheers!
Yes, I tried it. Error message says that the URL could not be resolved. Dead end.

---

### Post by ukripper on 2007-10-24
I havn't tried through repo yet

---

### Post by nisarg on 2007-10-24
Thank you Wieman01 and Ukripper.
So, the search continues...
I will remember to update the thread if I do come across a solution. 

BTW - If I do install it from a .deb package at the moment (missing out the updates) - How can I uninstall it and re-install it if/when we find the repository solution to work?

Thanks again.

---

### Post by jenhsun on 2007-10-24
Ya, I need realplayer too.
How about 64 bits version?

---

### Post by ukripper on 2007-10-24
Looks like we have to download the deb package as suggested by wieman01 I am not able to install it thru repos either.

---

### Post by wieman01 on 2007-10-24
> **nisarg said:**
> BTW - If I do install it from a .deb package at the moment (missing out the updates) - How can I uninstall it and re-install it if/when we find the repository solution to work?
It is:
> sudo dpkg -r realplay
Very simple in fact.

---

### Post by nisarg on 2007-10-24
Thanks.

> **wieman01 said:**
> It is:

Very simple in fact.

---

### Post by gustavoavellar on 2007-10-24
The repository gutsy-commercial is not working, yet. But you can add feisty-commercial to your sources.list even if you are running Ubuntu Gutsy (7.10). It will work, I've already tryed.

You just have to add the following line to your repository list:
```
deb http://archive.canonical.com/ubuntu feisty-commercial main
```
Then, to install Real Player:
```
sudo apt-get install realplay
```

--
Gustavo Avellar
[http://kiosky.blogspot.com](http://kiosky.blogspot.com)

---

### Post by nisarg on 2007-10-24
I tried installing it from S P M and get this error:
[I]realplayer:

Package realplayer has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list
[/I]
Am I missing something?
I havent tried it using the commands you have mentioned yet, will be giving it a try soon.
Cheers.

> **gustavoavellar said:**
> The repository gutsy-commercial is not working, yet. But you can add feisty-commercial to your sources.list even if you are running Ubuntu Gutsy (7.10). It will work, I've already tryed.

You just have to add the following line to your repository list:
```
deb http://archive.canonical.com/ubuntu feisty-commercial main
```
Then, to install Real Player:
```
sudo apt-get install realplay
```

--
Gustavo Avellar
[http://kiosky.blogspot.com](http://kiosky.blogspot.com)

---

### Post by ukripper on 2007-10-25
> **gustavoavellar said:**
> The repository gutsy-commercial is not working, yet. But you can add feisty-commercial to your sources.list even if you are running Ubuntu Gutsy (7.10). It will work, I've already tryed.

You just have to add the following line to your repository list:
```
deb http://archive.canonical.com/ubuntu feisty-commercial main
```
Then, to install Real Player:
```
sudo apt-get install realplay
```

--
Gustavo Avellar
[http://kiosky.blogspot.com](http://kiosky.blogspot.com)

Not recommended method though. It can break dependencies later on Gutsy if realplayer releases  further updates for feisty.

---

### Post by keith65 on 2007-10-25
Hi

Wieman01's advice works, but the version number changed from 10.0.8-0.1 to 10.0.9-0.1.

```
wget -c http://www.debian-multimedia.org/pool/main/r/realplay/realplayer_10.0.9-0.1_i386.deb
```


```
sudo dpkg -i realplayer_10.0.9-0.1_i386.deb
```

---

### Post by pyrforos on 2007-10-27
thanks mate!Ive been trying to find something for gutsy the last half hour...

---

### Post by ukripper on 2007-10-27
just instaled realplayer 10.0.9 installed just fine.

---

### Post by kostkon on 2007-10-27
The *commercial* repository was renamed to *partner*, thus the url for this new repository is
```
deb http://archive.canonical.com/ubuntu gutsy partner
```

---

### Post by wieman01 on 2007-10-27
> **kostkon said:**
> The *commercial* repository was renamed to *partner*, thus the url for this new repository is
```
deb http://archive.canonical.com/ubuntu gutsy partner
```
Can you install Realplayer from it? If so, I'll update my post. Thanks, mate.

---

### Post by aussieboss on 2007-10-28
Hey I know this is a pain in the butt but could someone who has successfully gotten real player installed give a step by step tutorial for a complete novice, assuming that i know nothing.  I just installed Gutsy and am very new to Ubuntu, so I don't know things like where the "repository" is, etc.  Thanks to anyone who can help!

---

### Post by wieman01 on 2007-10-28
> **aussieboss said:**
> Hey I know this is a pain in the butt but could someone who has successfully gotten real player installed give a step by step tutorial for a complete novice, assuming that i know nothing.  I just installed Gutsy and am very new to Ubuntu, so I don't know things like where the "repository" is, etc.  Thanks to anyone who can help!
Just open a terminal windows (command line) and follow instructions of post #24. Copy and paste the stuff into the terminal windows, press enter and type in your user password when prompted. Does that work for you?

---

### Post by peterthewolf on 2007-10-28
Non of these repositories seem to exist. Have you missed a step or have a misspelling

---

### Post by wieman01 on 2007-10-28
> **peterthewolf said:**
> Non of these repositories seem to exist. Have you missed a step or have a misspelling
Please try again... post #3.

---

### Post by ukripper on 2007-10-28
I have installed realplayer by folowing steps :


Open terminal window and type copy paste following line
```
wget -c http://www.debian-multimedia.org/pool/main/r/realplay/realplayer_10.0.9-0.1_i386.deb
```
Then copy paste this line :
```
 sudo dpkg -i realplayer_10.0.9-0.1_i386.deb
```

---

### Post by hieronymous on 2007-10-28
If you're running amd64 instead of i386, the debian-multimedia solution won't work. Instead, download the .bin file from [www.real.com/linux:](www.real.com/linux:)
```
wget http://www.real.com/realcom/R?href=http%3A%2F%2Fforms%2Ereal%2Ecom%2Freal%2Fplayer%2Fdownload%2Ehtml%3Ff%3Dunix%2FRealPlayer10GOLD%2Ebin
```
(Or just use your browser.) Then make it executable:
```
chmod a+x RealPlayer10GOLD.bin
```
and run the install script:
```
sudo ./RealPlayer10GOLD.bin
```
I specified /usr/local/RealPlayer for the installation path and /usr for the symbolic links. Works for both x86 and amd64.

---

### Post by cyneuron on 2007-10-29
why is real player not available in medibuntu or ubuntu commercial repo for it should had been till now.....i don't wish to install non-repo way....

---

### Post by ukripper on 2007-10-29
> **cyneuron said:**
> why is real player not available in medibuntu or ubuntu commercial repo for it should had been till now.....i don't wish to install non-repo way....

Then wait until it is in repo

---

### Post by ieffem on 2007-10-29
> **hieronymous said:**
> If you're running amd64 instead of i386, the debian-multimedia solution won't work. Instead, download the .bin file from [www.real.com/linux:](www.real.com/linux:)
```
wget http://www.real.com/realcom/R?href=http%3A%2F%2Fforms%2Ereal%2Ecom%2Freal%2Fplayer%2Fdownload%2Ehtml%3Ff%3Dunix%2FRealPlayer10GOLD%2Ebin
```
(Or just use your browser.) Then make it executable:
```
chmod a+x RealPlayer10GOLD.bin
```
and run the install script:
```
sudo ./RealPlayer10GOLD.bin
```
I specified /usr/local/RealPlayer for the installation path and /usr for the symbolic links. Works for both x86 and amd64.

Thanks, this works great!

---

### Post by anergy on 2007-10-29
> **hieronymous said:**
> If you're running amd64 instead of i386, the debian-multimedia solution won't work. Instead, download the .bin file from [www.real.com/linux:](www.real.com/linux:)
```
wget http://www.real.com/realcom/R?href=http%3A%2F%2Fforms%2Ereal%2Ecom%2Freal%2Fplayer%2Fdownload%2Ehtml%3Ff%3Dunix%2FRealPlayer10GOLD%2Ebin
```
(Or just use your browser.) Then make it executable:
```
chmod a+x RealPlayer10GOLD.bin
```
and run the install script:
```
sudo ./RealPlayer10GOLD.bin
```
I specified /usr/local/RealPlayer for the installation path and /usr for the symbolic links. Works for both x86 and amd64.

Thanks works for me as well; 
Those afraid of command line can go to directly [www.real.com]("www.real.com"). It will detect you are linux user. just click on the Free Download to download the RealPlayer10GOLD.bin file.
Right click on it and select **properties**. Go to the **Permissions** tab and check the execute:Allow...
Now simply double click it. It will create a directory called RealPlayer. Run the realplay file

---

### Post by wieman01 on 2007-10-29
> **anergy said:**
> Thanks works for me as well; 
Those afraid of command line can go to directly [www.real.com]("www.real.com"). It will detect you are linux user. just click on the Free Download to download the RealPlayer10GOLD.bin file.
Right click on it and select **properties**. Go to the **Permissions** tab and check the execute:Allow...
Now simply double click it. It will create a directory called RealPlayer. Run the realplay file
Interesting... actually we would need more of this type of instructions. Most (Windows) users are put off by command line, so I find your instructions very appealing in fact. It clearly demonstrates that there is a way to avoid command line after all if you don't like it.

---

### Post by robeec on 2007-11-01
you rule, weiman! i was trying to install realplayer since i upgraded to gutsy,
thanks!

---

### Post by rude_lee on 2007-11-01
thank you now im good love  ubuntu baby

---

### Post by joeally on 2007-11-10
do this:
```
sudo gedit /etc/apt/sources.list
``` 
and add this line to it
```
deb http://archive.canonical.com/ubuntu feisty-commercial main
```
then:
```
sudo apt-get update
```

then:
```
sudo apt-get install realplay
```

---

### Post by ka1ssr on 2007-11-10
After downloading RealPlayer10GOLD.bin from [www.real.com](www.real.com) and changing the execute permission bit, I get a "./RealPlayer10GOLD.bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory" error when I try to execute it.  Am I missing a package?

Thanks,

Bill

---

### Post by wieman01 on 2007-11-11
Try:
> sudo apt-get install libstdc++
Then execute ./RealPlayer10GOLD.bin.

---

### Post by toontastic on 2007-11-11
I get the error 

 realplayer depends on libstdc++5 (>= 1:3.3.4-1); however:
  Package libstdc++5 is not installed.

When trying to install realplayer. Any ideas how to install libstdc ?

---

### Post by wieman01 on 2007-11-11
> **toontastic said:**
> I get the error 

 realplayer depends on libstdc++5 (>= 1:3.3.4-1); however:
  Package libstdc++5 is not installed.

When trying to install realplayer. Any ideas how to install libstdc ?
See one post up...

---

### Post by toontastic on 2007-11-11
hehe read every post but that one :D thanks I'll give it a try

---

### Post by cosmofed on 2007-11-11
> **Anicka said:**
> Is realplayer available for gutsy? I cannot find it in medibuntu. Anyone knows if/when/where it will be?


Hi, I found it at [www.real.com/linux](www.real.com/linux). It's a binary file, but for some reason I can't get it to execute.
(Yes I changed the permissions and used the sudo account to execute; to no avail because it says it can't find it!)

This was after I installed the "libstdc++" package.

Good luck!

---

### Post by seanVT on 2007-11-11
> **cosmofed said:**
> Hi, I found it at [www.real.com/linux](www.real.com/linux). It's a binary file, but for some reason I can't get it to execute.
(Yes I changed the permissions and used the sudo account to execute; to no avail because it says it can't find it!)

This was after I installed the "libstdc++" package.

Good luck!


Hi,

If it can't find it, the obvious thing to ask is if you're in the same directory with it and - did you type the case-sensitive filename exactly the same? (i just selected the name of it with the mouse and paested it into the prompt instead of typing the command. It did install just fine.).

---

### Post by wieman01 on 2007-11-11
> **cosmofed said:**
> Hi, I found it at [www.real.com/linux](www.real.com/linux). It's a binary file, but for some reason I can't get it to execute.
(Yes I changed the permissions and used the sudo account to execute; to no avail because it says it can't find it!)

This was after I installed the "libstdc++" package.

Good luck!
You need to make it an executable by changing the file permissions from command line:
> sudo chmod +x <file_name>
Then execute it:
> sudo ./<file_name>

---

### Post by cosmofed on 2007-11-11
Thanks for your patience on this simple and frustrating issue. I have downloaded RealPlayer to my home folder. From the home folder I can "see" the  binary but when I execute it, it still can't find it? Is this the Twlight Zone or am I just stupid?

cos@cos-laptop:~$ ls -l
total 5700
drwxr-xr-x 3 cos cos    4096 2007-11-07 19:59 bcm43xx
drwxrwxrwx 3 cos cos    4096 2007-11-11 12:14 Desktop
drwxr-xr-x 2 cos cos    4096 2007-11-06 21:54 Documents
lrwxrwxrwx 1 cos cos      26 2007-11-06 13:47 Examples -> /usr/share/example-content
drwxr-xr-x 2 cos cos    4096 2007-11-06 21:54 Music
-rw-r--r-- 1 cos cos       0 2007-11-08 21:12 nautilus-debug-log.txt
drwxr-xr-x 2 cos cos    4096 2007-11-06 21:54 Pictures
drwxr-xr-x 2 cos cos    4096 2007-11-06 21:54 Public
-rwxr-xr-x 1 cos cos 5790356 2007-08-09 12:36 RealPlayer10GOLD.bin
drwxr-xr-x 2 cos cos    4096 2007-11-06 21:54 Templates
drwxr-xr-x 2 cos cos    4096 2007-11-06 21:54 Videos
cos@cos-laptop:~$ sudo ./RealPlayer10GOLD.bin
sudo: unable to execute ./RealPlayer10GOLD.bin: No such file or directory
cos@cos-laptop:~$

---

### Post by seanVT on 2007-11-11
> **cosmofed said:**
> Thanks for your patience on this simple and frustrating issue. I have downloaded RealPlayer to my home folder. From the home folder I can "see" the  binary but when I execute it, it still can't find it? Is this the Twlight Zone or am I just stupid?

cos@cos-laptop:~$ ls -l
total 5700
drwxr-xr-x 3 cos cos    4096 2007-11-07 19:59 bcm43xx
drwxrwxrwx 3 cos cos    4096 2007-11-11 12:14 Desktop
drwxr-xr-x 2 cos cos    4096 2007-11-06 21:54 Documents
lrwxrwxrwx 1 cos cos      26 2007-11-06 13:47 Examples -> /usr/share/example-content
drwxr-xr-x 2 cos cos    4096 2007-11-06 21:54 Music
-rw-r--r-- 1 cos cos       0 2007-11-08 21:12 nautilus-debug-log.txt
drwxr-xr-x 2 cos cos    4096 2007-11-06 21:54 Pictures
drwxr-xr-x 2 cos cos    4096 2007-11-06 21:54 Public
-rwxr-xr-x 1 cos cos 5790356 2007-08-09 12:36 RealPlayer10GOLD.bin
drwxr-xr-x 2 cos cos    4096 2007-11-06 21:54 Templates
drwxr-xr-x 2 cos cos    4096 2007-11-06 21:54 Videos
cos@cos-laptop:~$ sudo ./RealPlayer10GOLD.bin
sudo: unable to execute ./RealPlayer10GOLD.bin: No such file or directory
cos@cos-laptop:~$

Certainly looks like the right file name. It's seems strange that your sudo command didn't ask you for a password or make you root anyway. Why don't you try doing ./RealPlayer10GOLD.bin without the sudo? And if you get permission problems, do "sudo su" to become root first. And then do ./RealPlayer10GOLD.bin. Sorry if I'm barking up the wrong tree here...

---

### Post by cosmofed on 2007-11-11
Thanks for the quick replay seanVT. Trying your suggestions, nada:

cos@cos-laptop:~$ sudo ./RealPlayer10GOLD.bin
[sudo] password for cos:
Sorry, try again.
[sudo] password for cos:
sudo: unable to execute ./RealPlayer10GOLD.bin: No such file or directory
cos@cos-laptop:~$ sudo su
root@cos-laptop:/home/cos# ./RealPlayer10GOLD.bin
bash: ./RealPlayer10GOLD.bin: No such file or directory
root@cos-laptop:/home/cos# ls -l
total 5700
drwxr-xr-x 3 cos cos    4096 2007-11-07 19:59 bcm43xx
drwxrwxrwx 3 cos cos    4096 2007-11-11 13:22 Desktop
drwxr-xr-x 2 cos cos    4096 2007-11-06 21:54 Documents
lrwxrwxrwx 1 cos cos      26 2007-11-06 13:47 Examples -> /usr/share/example-content
drwxr-xr-x 2 cos cos    4096 2007-11-06 21:54 Music
-rw-r--r-- 1 cos cos       0 2007-11-08 21:12 nautilus-debug-log.txt
drwxr-xr-x 2 cos cos    4096 2007-11-06 21:54 Pictures
drwxr-xr-x 2 cos cos    4096 2007-11-06 21:54 Public
-rwxr-xr-x 1 cos cos 5790356 2007-08-09 12:36 RealPlayer10GOLD.bin
drwxr-xr-x 2 cos cos    4096 2007-11-06 21:54 Templates
drwxr-xr-x 2 cos cos    4096 2007-11-06 21:54 Videos
root@cos-laptop:/home/cos# 

Any other suggestions?

---

### Post by wieman01 on 2007-11-11
Where does Firefox normally download to? Please choose another folder, e.g. Desktop.

This sometimes happens to me as well. I would download to my Desktop, but then won't find it there. I don't why that is so, but I can confirm it.

What if you downloaded it to an USB device?

---

### Post by seanVT on 2007-11-12
> **cosmofed said:**
> Thanks for the quick replay seanVT. Trying your suggestions, nada:

cos@cos-laptop:~$ sudo ./RealPlayer10GOLD.bin
[sudo] password for cos:
Sorry, try again.
[sudo] password for cos:
sudo: unable to execute ./RealPlayer10GOLD.bin: No such file or directory
cos@cos-laptop:~$ sudo su
root@cos-laptop:/home/cos# ./RealPlayer10GOLD.bin
bash: ./RealPlayer10GOLD.bin: No such file or directory
root@cos-laptop:/home/cos# ls -l
total 5700
drwxr-xr-x 3 cos cos    4096 2007-11-07 19:59 bcm43xx
drwxrwxrwx 3 cos cos    4096 2007-11-11 13:22 Desktop
drwxr-xr-x 2 cos cos    4096 2007-11-06 21:54 Documents
lrwxrwxrwx 1 cos cos      26 2007-11-06 13:47 Examples -> /usr/share/example-content
drwxr-xr-x 2 cos cos    4096 2007-11-06 21:54 Music
-rw-r--r-- 1 cos cos       0 2007-11-08 21:12 nautilus-debug-log.txt
drwxr-xr-x 2 cos cos    4096 2007-11-06 21:54 Pictures
drwxr-xr-x 2 cos cos    4096 2007-11-06 21:54 Public
-rwxr-xr-x 1 cos cos 5790356 2007-08-09 12:36 RealPlayer10GOLD.bin
drwxr-xr-x 2 cos cos    4096 2007-11-06 21:54 Templates
drwxr-xr-x 2 cos cos    4096 2007-11-06 21:54 Videos
root@cos-laptop:/home/cos# 

Any other suggestions?

That's really weird. Next thing I would try is renaming it. Something's going on with the name. Right-click on it in Nautilus and rename it abc.bin and try to run it then.

---

### Post by cosmofed on 2007-11-12
Firefox is saving downloaded files to the desktop. I tried running it from there and when that didn't work I moved it to other places. In all cases I made sure any folder and of course the Realplayer binary was set to execute.

I also tried renaming the binary file to something else, and even moved it to a USB drive. No luck!

Well, I think the most frustrating thing about this is not knowing why this doesn't work. So I think I'm going to pass on RealPlayer and not waste any more time on it. I'm new to Ubunto and have lots of other things to learn in my quest to totally ween myself from the borg.

The Ubunto community is great. Thanks for all your help!

---

### Post by ukripper on 2007-11-13
> **cosmofed said:**
> Firefox is saving downloaded files to the desktop. I tried running it from there and when that didn't work I moved it to other places. In all cases I made sure any folder and of course the Realplayer binary was set to execute.

I also tried renaming the binary file to something else, and even moved it to a USB drive. No luck!

Well, I think the most frustrating thing about this is not knowing why this doesn't work. So I think I'm going to pass on RealPlayer and not waste any more time on it. I'm new to Ubunto and have lots of other things to learn in my quest to totally ween myself from the borg.

The Ubunto community is great. Thanks for all your help!

Try changing permissions-
Goto directory where you have saved your file

then type  ```
sudo chmod 777 RealPlayer10GOLD.bin 
```

and then follow instructions for installtion

---

### Post by cosmofed on 2007-11-13
ukripper,
    That was it! Thank you.

---

### Post by ukripper on 2007-11-14
Glad it worked out for you!

---

### Post by texasred218 on 2007-11-16
Thank you guys for this  how to  I love the ubuntu& linux forums

---

### Post by sourcemorph on 2007-11-26
hey i download the .deb installation file of real player 10.0.9.809 (gold) frm dc++ in my college... i installed properly but the video freezes much too often...

any ideas wht can be done?

---

### Post by ukripper on 2007-11-27
> **sourcemorph said:**
> hey i download the .deb installation file of real player 10.0.9.809 (gold) frm dc++ in my college... i installed properly but the video freezes much too often...

any ideas wht can be done?

try reinstalling it first

---

### Post by Mateo on 2007-12-02
Helix/Real are nice low resource media players... the downside is that they don't seem to play anything.  Don't play divx, don't play xvid.  Helix won't play real videos but real player will (luckily), but those videos aren't very common any more.

---

### Post by ukripper on 2007-12-03
> **Mateo said:**
> Helix/Real are nice low resource media players... the downside is that they don't seem to play anything.  Don't play divx, don't play xvid.  Helix won't play real videos but real player will (luckily), but those videos aren't very common any more.

use VLC or mplayer for other stuff.

---

### Post by Lvcoyote on 2007-12-03
Guys, I got real player installed using the "Make the bin file executable" method.  But I dont see where I can launch the program after installing.  It doesnt show up in sound and video applications.....  So how do I start the program and how can I make it show in sound and video applications menu???

---

### Post by wieman01 on 2007-12-04
> **Lvcoyote said:**
> Guys, I got real player installed using the "Make the bin file executable" method.  But I dont see where I can launch the program after installing.  It doesnt show up in sound and video applications.....  So how do I start the program and how can I make it show in sound and video applications menu???
I have got KDE so I can't help you, however, you could try and launch it from command line issuing:
> realplay
Or...
> realplayer

---

### Post by Lvcoyote on 2007-12-04
I ended up installing the package from the command line and it works fine now.

---

### Post by lvdude on 2007-12-08
Hey, I've read all the posts, but as of yet haven't found a solution that will allow me to install real player. If I try executing the .bin file I get the  error message: 
"bash: ./RealPlayer10GOLD.bin: No such file or directory" (The file does have x-permissions). Via the repository method I get: 
"r@leohr:~$ sudo apt-get install realplayer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package realplayer is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package realplayer has no installation candidate"
Does anyone have any advice? I'm completely stumped.
Thanks.

---

### Post by wieman01 on 2007-12-09
Wihle you execute...
> ./RealPlayer10GOLD.bin
...have you downloaded the file beforehand? It appears the file simply isn't there...

---

### Post by evil_cat on 2007-12-09
Step 1:
Dpkg your realplayer packages

Step2:

Once this is done return to your deb package, the aim is to get the 'nphelix.so' and to copy it in the /usr/lib/mozilla/plugins

So just right on the realplayer package and open with archives manager -->data.taz.gz-->usr-->lib-->mozilla--->plugins--->extract nphelix and copy it in /usr/lib/mozilla

That's how it works out for me

---

### Post by david.rahrer on 2007-12-19
If anyone is still having trouble installing RealPlayer in Gutsy, here is the easy method if you are using a default Gutsy 32-bit (i386) installation and Firefox is your browser: 

Close Firefox.  Click [here]("http://www.debian-multimedia.org/pool/main/r/realplay/realplayer_10.0.9-0.1_i386.deb") and chose to open with GDebi Package Installer instead of download.  After install completes, open Terminal and type the following:

> sudo ln -s /usr/lib/mozilla/plugins/nphelix.so /usr/lib/firefox/plugins/nphelix.so

and

> sudo ln -s /usr/lib/mozilla/plugins/nphelix.xpt /usr/lib/firefox/plugins/nphelix.xpt

You will need to enter your password, but otherwise it is painless.  I don't know if this will work on 64-bit as I'm not using it.  This is just a combination of the download listed at the beginning of the thread and the easiest solution I could find for the misplaced browser plugins.  It has worked for me.

Test Browser Plugin

I think you need to run RealPlayer at least once before doing this, so just go to Applications -> Sound and Video -> RealPlayer 10 and go through the first screen or two until it's happy, then close.  Now go [here]("http://cita.rehab.uiuc.edu/mozilla/ts-test-page-embed.php") and see if the RealPlayer screen appears embedded (there is no media, just the logo).  If so, the plugin links should be working.

---

### Post by LeslieL on 2007-12-19
I've got RealPlayer installed and seemingly playing, but there's no sound. I have sound in Rhythmbox and other media players. Any clues?

---

### Post by vigyani on 2007-12-26
Hi

I followed the post #24 to install realplayer on Ubuntu 7.10 Gutsy on Acer Aspire 4710. It works fine.

thanks
Vig

---

### Post by silent1977 on 2007-12-31
> **wieman01 said:**
> Sorry, that was for Feisty... Try this instead:
```
wget -c http://www.debian-multimedia.org/pool/main/r/realplay/realplayer_10.0.9-0.1_i386.deb
```
```
sudo dpkg -i realplayer_10.0.8-0.1_i386.deb
```
This is the reference: [http://www.howtoforge.com/the_perfect_desktop_ubuntu_gutsy_gibbon_p6]("http://www.howtoforge.com/the_perfect_desktop_ubuntu_gutsy_gibbon_p6")

hey guys, i try to install real player in my Ubuntu but failed. I follow the instruction you gave gets below error.

ERROR 404. NOT FOUND.

Then i try to dl realplayer.bin but also failed to install. What is the problem?? Kindly help, I'm new to Ubuntu. Thanks

---

### Post by AgentZ86 on 2007-12-31
HI all, 

Quick question why won't the helix player from the applications add/remove section play the realvideo , I got the same message that I got with totem etc.

(Couldn't find a realvideo shared library for version 4)

So it's no big deal, I just wend to the Realplayer site and installed the RealPlayer10GOLD.bin, I downloaded it to my desktop, then made it executable.

And works perfectly, but now I got these folders with codecs and things on my desktop.

I'm afraid to get rid of it cause I don't want to hurt my working install of RealPlayer.

Any recommendations ? Can I delete the folder ? or now what ?

And is there a way to just make the realvideo shared library for version 4 work on helix instead ?

---

### Post by bharadwaj on 2007-12-31
> **Anicka said:**
> Thank you wieman! It worked like a charm. Now I can listen to my favourite webradio again.
If thats the webradio you want to listen then try LastFM very compact one and has an integration with AWN navigator also

---

### Post by aonegodman on 2008-01-01
Thought I'd give it try.

First the adding the "wget -c . . . ."  line to my sources.lst didn't work for me in the original post.

I got some unrecognized error feedback in Terminal when trying to update the list.

Anyway, I jumped over to the source link *[www.debian-multimedia.org](www.debian-multimedia.org)* and  took a look.

Here's what I found:
The first package to install is debian-multimedia-keyring.
You have two choices :

1
With dpkg :
Download the debian-multimedia-keyring. package by hand (right click and Save Link As...) and install the package with 'dpkg -i debian-multimedia-keyring_2007.02.14_all.deb'

2
With apt-get :
apt-get install debian-multimedia-keyring

I was able to just download the deb file and double click on it and Package Installer did the install for me.

Next I added the next line to my source.lst file:

[I]deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) stable main
[/I]

Read down through the list on website page and choose your flavor.

Next I did - *** sudo apt-get update***

Then did this -  ***sudo apt-get install realplayer***

That seemed to do it for me. Followed the Realplayer install windows <click> <click> and it popped up on my desktop ready to go.

Gonna go check it out with Browser and see what's up. Get back later.

Just another way to get to the desired results others have offered. Hope this helps somebody.




And ignore the apt-get warnings about the missing GPG key.

---

### Post by arnicainthemembrane on 2008-01-02
It looks like

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy-commercial main

Is outdated and won't make the commercial repo available in Gutsy. Is there another way to get access to the commercial repository?

thanks...

---

### Post by ljd65536 on 2008-01-06
I could not get realplayer via apt-get. So I converted the rpm from real.com to a deb using alien. But it would not play because it needed an older libstdc++. I found the solution below and now it seems to work. This must be done with great care as you messing around in the standard library director /usr/lib. But I don't think it should have any bad side effects because  the gcc library versioning is very robust.

[http://voiceofchinese.com/forum/installed-realplayer-for-ubuntu-linux-with-libstdc-so-5](http://voiceofchinese.com/forum/installed-realplayer-for-ubuntu-linux-with-libstdc-so-5)

---

### Post by jslmg on 2008-01-09
I installed Real Player by the methods described in this thread about a week ago. At first, it worked fine. I was able to watch VOA TV and listen to BBC world service. But now, for some reason, the app is broken in my Gutsy. If I click on any menu in the menubar, the app crashes.

Anyone else having this experience?

Also, a question: What is the difference between Real Player and Helix Player? Will Helix Player play .ram files, for example, and why aren't we all using that?

---

### Post by jslmg on 2008-01-09
An Update: 

I just installed Helix Player, which is available in Synaptic. To do this, I had to uninstall Realplayer (automatically removed). 

However, Helix crashes, too. Clicking on anything in the menubar crashes it.

Can anybody help me get Real Player/Helix Player working again?

---

### Post by Matej_C. on 2008-01-09
have anybody of you tryed to install it with automatix??? the best click-click solution :lolflag:

---

### Post by wieman01 on 2008-01-09
> **Matej_C. said:**
> have anybody of you tryed to install it with automatix??? the best click-click solution :lolflag:
No, it's not. Automatix means trouble, Gutsy should be perfectly fine. I would not recommend it as it can seriously bork your system...

---

### Post by LeslieL on 2008-01-09
I had a day or two of sound and now it's gone. Was there an update that screwed it up?

---

### Post by jslmg on 2008-01-09
bump-uh-de-bump...

> **jslmg said:**
> An Update: 

I just installed Helix Player, which is available in Synaptic. To do this, I had to uninstall Realplayer (automatically removed). 

However, Helix crashes, too. Clicking on anything in the menubar crashes it.

Can anybody help me get Real Player/Helix Player working again?

---

### Post by cor2y on 2008-01-09
You don't need real player or Helix to play real media files.
Just the w32codecs from the restricted repos and the right plugins if its gstreamer or xine (for xine-ui you have to point to where the w32codecs are installed) and the media player of your choice (excluding vlc and ffmpeg's ffplay) xine, gxine, totem-xine, mplayer, totem-gstreamer can all play real media files once the w32codecs are installed and the correct plugins aka all for gstreamer.

---

### Post by jslmg on 2008-01-10
Thanks! Yes, actually, I just discovered this through further investigation. I've now got Gxine running, playing most streams, but with some issues that need to be ironed out.

Here's one I'm dealing with right now:

I mostly need RealPlay compatibility to hear BBC World Service and some on-line video, likeNASA, VOA TV and DW-TV. With BBC World Service, particularly, I'm noticing that the stream plays for about 2 minutes, then stops. That's not the case in Mac OS X, which is on the same computer and using the same Internet connection. Anyone else experiencing this? Any remedies?

BTW, the Real/Helix crashing was due to macmenu. After disabling macmenu, they didn't crash anymore. But because I want a fully functioning desktop with macmenu, I'm switching to Gxine.

---

### Post by jslmg on 2008-01-10
Also, I'm still having most Internet video crashing Gxine, despite having installed the w32codecs. Gxine goes gray then crashes. why?

---

### Post by jslmg on 2008-01-12
Can anyone help me, then, with these two issues:

1) When listening to a .ram stream such as BBC World Service, the stream plays for about 2 minutes, then stops. That's not the case in Mac OS X, which is on the same computer and using the same Internet connection.

2) Video streams, such as VOA TV or NASA, crash Gxine as they start.

---

### Post by ubuntu-freak on 2008-01-13
I think Helix is needed for ram streams. 
 
Give MPlayer a try. I posted a how-to here, it's the best solution once it is setup
 
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)
 
I rarely have problems streaming. If my how-to solves your problems (it should) please reply in that thread too as it keeps it alive. Plus I like when people get things working.
 
Nathan

---

### Post by jslmg on 2008-01-13
Thanks, nathan. I'll get to work on configuring Mplayer. 

Since that post, I got Gxine working better. Turns out that Gxine will often--though not always--crash if it can't connect to a stream.

I went hunting for working MRLs, and so I was able to get most of my favorite .rm streams working in Gxine. VOA, NASA, CSPAN, are all working at the moment. Still buggy as hell, though! Sometimes I still have to restart Gxine a couple of times cuz of crashes.

I got totem working well for non-.rm streaming video, like .asx, .asf, and so on. Streams like France24, ClassicArts, ABCNow, CCTV9 are coming in well there.

Would be great to have one player that will work for all. I've got Mplayer, but haven't had much success with it. I'll give your HOWTO a go!

---

### Post by jslmg on 2008-01-13
I just followed the HOWTO on Mplayer. Sorry to say it didn't make much difference in terms of what I need to do--pretty much the same state as before.

Even with the configuration given in the HOWTO, I can't open asx, wmv, or asf streams in Mplayer--Totem Movie Player is still handling those.

I can't open .rm or rtsp streams in Mplayer--Gxine still handles those. I'll be trying Helix player shortly--my macmenubar has crashed, and until I get that back, at least, I can use Helix or RealPlayer.

I am now able to view BBC videos through Firefox using the Gxine plugin. That's an improvement over before, but doesn't seem connected to this Mplayer configuration.

---

### Post by jslmg on 2008-01-13
> **jslmg said:**
>  I'll be trying Helix player shortly--my macmenubar has crashed, and until I get that back, at least, I can use Helix or RealPlayer.

Actually, I reverted to Real Player 10, installed easily using post #24 in this thread. 

Problem is: I've got no sound in Real Player. I do have it in Gxine, though.

 I'd like to use Real Player cuz of all the crashes I get with Gxine. Any suggestions on getting sound in Real Player?

---

### Post by ubuntu-freak on 2008-01-13
I've found Helix is working better than Realplayer so stay with Helix. That's why Realplayer isn't in the repo anymore. 
 
How can totem etc be handling some streams? Did you actually follow my how-to? You can ONLY have mozilla-mplayer and mozilla-helix-player installed. NOT totem-mozilla or vlc etc. Remove them!
 
Hope that helps,
 
Nathan

---

### Post by jslmg on 2008-01-13
> **reassuringlyoffensive said:**
> I've found Helix is working better than Realplayer so stay with Helix.

The problem with Helix is that wouldn't load the .rm or .ram streams I need. In fact, a window opening telling me to get RealPlayer to play those. So, OK, that was the most direct way. Is it easy to change the config in Helix to get it to play all the file types that RealPlayer does? If I can do that, then, yes, of course, I'll prefer the open-source app.
 
> How can totem etc be handling some streams? Did you actually follow my how-to? You can ONLY have mozilla-mplayer and mozilla-helix-player installed. NOT totem-mozilla or vlc etc. Remove them!

I'll check again. I did follow every step you gave in that first post, including removing all the programs you said to remove, and deleting all the entries in the mplayer config file and pasting in your settings.

Is there more in subsequent posts in that thread? I'll check that too.

---

### Post by jslmg on 2008-01-13
> **reassuringlyoffensive said:**
> You can ONLY have mozilla-mplayer and mozilla-helix-player installed. NOT totem-mozilla or vlc etc. Remove them!

Just checked Synaptic to see what was installed and what wasn't. 

totem-mozilla and totem-xine are not installed, but totem-gstreamer and totem are.

mozilla-plugin-vlc is also not installed.

BTW, web video on sites such as the BBC is currently being handled by the xine-plugin. 

I did get an .rm stream to open in Mplayer, but no sound. Come to think of it, I've got the same problem in RealPlayer--good video, no sound.

It's simply a fact that Mplayer won't load any WMV or ASX streams, even if I paste them into the player's "open" window. Mplayer just sits there. Totem Movie Player is still handling all those.

Here's  my mplayerplug-in.conf:

download=1
keep-download=1
cachesize=1024
cache-percent=25
dload-dir=$HOME
noembed=0
autoplay=1
enable-wmp=1
enable-qt=1
enable-rm=1
enable-gmp=1
enable-dvx=1
enable-mpeg=1
enable-mp3=1
enable-midi=0
enable-pls=1
enable-ogg=1
enable-smil=1
enable-helix=1
nomediacache=0
nopauseonhide=0
rtsp-use-tcp=0
rtsp-use-http=0

I would like to get this working--an all-in-one player would be fantastic!

---

### Post by ubuntu-freak on 2008-01-13
Did you actually install the win32codecs? What happens when you click on a stream?
 
Here's a tip I posted somewhere else.
 

Some people have to remove a certain file from the /home/.firefox folder. I don't remember what though. Save your bookmarks and delete the folder, then reinstall FF and mozilla mplayer, helix plugins. Then check your config is the same (should be). Did you remove Realplayer? Should've been removed automatically when Helix was installed though.
 
Nathan

---

### Post by jslmg on 2008-01-13
> **reassuringlyoffensive said:**
> Did you actually install the win32codecs?
win32codecs are installed, enabling WM-type files in Totem and .rm media in general.

>  What happens when you click on a stream?
When I click on an realmeadia-type stream in Firefox, it opens in the browser with xine-plugin. WMV...haven't seen that yet. Most media on the web, such as CNN video or youtube, is flash-based. Flash is an unrelated issue.
 
> Some people have to remove a certain file from the /home/.firefox folder. I don't remember what though. Save your bookmarks and delete the folder, then reinstall FF and mozilla mplayer, helix plugins. Then check your config is the same (should be).
Yikes! All that? OK, I'll give it a try a little later and let you know what happens. I'll peek into the folder first, though, and see if any file seems obvious.

> Did you remove Realplayer? Should've been removed automatically when Helix was installed though.
Well, here's the thing: I uninstalled Helix and reinstalled Real after doing your steps cuz Helix wasn't loading the .rm streams I needed. If I could figure out how to configure Helix to load .rm/ram streams, I'd go back to Helix. Besides, I'm not getting sound in Real Player, though I am in gxine, so I'd like to give helix a try. Any hints?

---

### Post by ubuntu-freak on 2008-01-13
I thought you removed the xine plugin? That's your problem.
 
Uninstall that and check /usr/lib/firefox/plugins. 

Helix is configured in mplayerplugin conf (enable helix, divx, mp3 etc).
 
Nathan

---

### Post by jslmg on 2008-01-14
Well, I haven't had any success with mplayer. 

After removing xine-plugin, the mplayer plugin did take its place in Firefox, but I got no video or sound--only a message saying the mplayer plugin had loaded.

In Mplayer GUI, I have not been able to get any type of file or stream to play, despite having done all the steps in Nathan's HOWTO. I think part of the problem may be in how my Ubuntu system is configured for video and audio output, and it looks like I would have to match up the settings in Mplayer with the settings in my system...a daunting task.

At this point, it looks like Gxine is the most reliable and versatile player on my system. It loads both Windows-Media type files and RealPlayer type files, which is quite a bit better even than any player on the Mac platform, which is where I'm migrating from. And it plays over my system without any need to reconfigure.

I reinstalled xine-plugin and am now once again able to view BBC videos over Firefox.

I'll stick with gxine for the time being, until a better solution is found. It looks like it does what Mplayer should do--play all video and audio formats--and it does it with much less effort from the user, at least on my system.

---

### Post by ubuntu-freak on 2008-01-14
> **jslmg said:**
> Well, I haven't had any success with mplayer. 

After removing xine-plugin, the mplayer plugin did take its place in Firefox, but I got no video or sound--only a message saying the mplayer plugin had loaded.

In Mplayer GUI, I have not been able to get any type of file or stream to play, despite having done all the steps in Nathan's HOWTO. I think part of the problem may be in how my Ubuntu system is configured for video and audio output, and it looks like I would have to match up the settings in Mplayer with the settings in my system...a daunting task.

At this point, it looks like Gxine is the most reliable and versatile player on my system. It loads both Windows-Media type files and RealPlayer type files, which is quite a bit better even than any player on the Mac platform, which is where I'm migrating from. And it plays over my system without any need to reconfigure.

I reinstalled xine-plugin and am now once again able to view BBC videos over Firefox.

I'll stick with gxine for the time being, until a better solution is found. It looks like it does what Mplayer should do--play all video and audio formats--and it does it with much less effort from the user, at least on my system.

 
That's very odd. Even the main app itself doesn't work? Sounds like it can't find the win32codecs. That's what you need to look into. I presume you installed them. Check the win32 folder in /usr/lib.
 
Nathan

---

### Post by jslmg on 2008-01-14
> **reassuringlyoffensive said:**
> That's very odd. Even the main app itself doesn't work? Sounds like it can't find the win32codecs. That's what you need to look into. I presume you installed them. Check the win32 folder in /usr/lib.

Yes, I installed win32codecs a few days ago... had to before I could gxine working.

---

### Post by Bablefish on 2008-01-14
I have a link to an official WIKI that has a link to a download of Real Player.deb file and it still works

[https://help.ubuntu.com/community/RealplayerInstallationMethods](https://help.ubuntu.com/community/RealplayerInstallationMethods)

---

### Post by ubuntu-freak on 2008-01-14
> **jslmg said:**
> Yes, I installed win32codecs a few days ago... had to before I could gxine working.

I've made changes to my how-to. Try it all again from scratch.

Nathan

---

### Post by ubuntu-freak on 2008-01-14
> **Bablefish said:**
> I have a link to an official WIKI that has a link to a download of Real Player.deb file and it still works

[https://help.ubuntu.com/community/RealplayerInstallationMethods](https://help.ubuntu.com/community/RealplayerInstallationMethods)

Is it really needed though? I watch rm streams and listen to ram radio all the time and I only use win32codecs + mozilla-mplayer.

Works sweet for me. Try my how-to.

Nathan

---

### Post by Bablefish on 2008-01-14
The thing about it is Real Player is the only thing that plays Real Media sound files, and so far it's the only thing I know that works with sites using Real Player.

---

### Post by ubuntu-freak on 2008-01-14
> **Bablefish said:**
> The thing about it is Real Player is the only thing that plays Real Media sound files, and so far it's the only thing I know that works with sites using Real Player.

Not true. I don't have RealPlayer and I'm listening to an ram radio stream right now and have watched some rm video streams today as well. You only need win32codecs and mozilla-mplayer.

Nathan

---

### Post by cor2y on 2008-01-14
Yes you don't need real media player to playback real media files.
Just the correct plugins for the media player of choice.
For example xine-ui needs to know where the real codecs are aka w32codecs (just install that restricted package).
Totem-gstreamer requires i'd say all its plugins ugly, multiverse etc.
Mplayer the w32codecs, even helix requires a plugin to playback real media files it won't by default.

---

### Post by ubuntu-freak on 2008-01-14
> **cor2y said:**
> Yes you don't need real media player to playback real media files.
Just the correct plugins for the media player of choice.
For example xine-ui needs to know where the real codecs are aka w32codecs (just install that restricted package).
Totem-gstreamer requires i'd say all its plugins ugly, multiverse etc.
Mplayer the w32codecs, even helix requires a plugin to playback real media files it won't by default.

 
Well said! 
 
How is your streaming performance? Try my how-to if you want.
 
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)
 
Nathan

---

### Post by ubuntu-freak on 2008-01-18
Okay I have RealPlayer now. MPlayer was far too unpredictable handling RM streams.
 
Check out my how-to and fix for RealPlayer
 
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)
 
Nathan

---

### Post by jslmg on 2008-01-18
> **reassuringlyoffensive said:**
> Okay I have RealPlayer now. MPlayer was far too unpredictable handling RM streams.
 
Check out my how-to and fix for RealPlayer
 
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)
 
Nathan

I've actually enjoyed using gxine since I got it all configured--quite reliable for both WM type files and RM files. doesn't crash that often, really. And it's open source, unlike Real Player.

---

### Post by ubuntu-freak on 2008-01-18
> **jslmg said:**
> I've actually enjoyed using gxine since I got it all configured--quite reliable for both WM type files and RM files. doesn't crash that often, really. And it's open source, unlike Real Player.

 
RealPlayer for Linux is open source. Was made by the open source community. It's the same as Helix except that it uses propriatry codecs. So it's just the codecs that aren't open source I think.
 
Nathan

---

### Post by eye208 on 2008-01-18
I wonder what content is out there that isn't available as WMV so it makes RealPlayer worth to be installed.

AFAIK the RealMedia format is pretty much dead. The world has been shifting away from it and towards FLV, WMV and MP4 for quite some time now. Even the Flash plugin for web browsers now supports MP4 (with H.264 video and AAC or MP3 audio content).

---

### Post by jslmg on 2008-01-18
> **eye208 said:**
> I wonder what content is out there that isn't available as WMV so it makes RealPlayer worth to be installed.

AFAIK the RealMedia format is pretty much dead. The world has been shifting away from it and towards FLV, WMV and MP4 for quite some time now. Even the Flash plugin for web browsers now supports MP4 (with H.264 video and AAC or MP3 audio content).

Well, a number of media providers still use it. It may be more common in Europe, though. BBC still uses Real servers for all its netcasts. Deutsche Welle TV, VOA, NASA (though also available in WM). These are just a few of the major Internet TV streams using it. I listen to/watch these quite a bit, so I need Real Media compatibility.

---

### Post by eye208 on 2008-01-18
> **jslmg said:**
> BBC still uses Real servers for all its netcasts.
They let you choose between RM and WMV.

> Deutsche Welle TV
RM, WMV, Flash.

> NASA (though also available in WM)
Exactly my point.

You need not use RealMedia. Even the Windows crowd considers RM a dying format. By using RealPlayer on Linux, you are only prolonging its (well deserved) death.

---

### Post by ubuntu-freak on 2008-01-18
> **eye208 said:**
> They let you choose between RM and WMV.


RM, WMV, Flash.


Exactly my point.

You need not use RealMedia. Even the Windows crowd considers RM a dying format. By using RealPlayer on Linux, you are only prolonging its (well deserved) death.

 
Radio sounds better in Real format on the BBC for some reason and their wmv videos behave a bit strangely. Plus there are some stupid stations that only offer ram.

BBC should do mp3 and ogg streaming radio only. 

Nathan

---

### Post by Dolmio on 2008-01-26
> **wieman01 said:**
> Open the repositories file:

Add this line:
```
deb http://archive.canonical.com/ubuntu feisty-commercial main
```
Then update:

And install Realplayer:

Thanks wieman01. Works perfectly even on a Gutsy :-)

Dolmio

---

### Post by ubuntu-freak on 2008-01-26
> **Dolmio said:**
> Thanks wieman01. Works perfectly even on a Gutsy :-)

Dolmio

 
You probably shouldn't keep a Fiesty repo in your sources list.
 
If anyone else wants RealPlayer and general streaming, multimedia and video help, try my easy how-to
 
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)
 
There is also a fix for RealPlayer if it behaves strangely on your system (stutters, freezes).
 
Nathan

---

### Post by popatopalous on 2008-03-01
> **reassuringlyoffensive said:**
> Not true. I don't have RealPlayer and I'm listening to an ram radio stream right now and have watched some rm video streams today as well. You only need win32codecs and Helix Mozilla.

Nathan

There are sites like RTE [Ireland] that won't play with any thing except Realplayer. Realplayer is needed for some of us. As far as I can tell it is impossible to get Realplayer to work in Firefox in 64 bit Kubuntu. If any one has please tell me how.

Edit: [http://www.rte.ie/radio/index.html](http://www.rte.ie/radio/index.html)

Edit #2: I forgot to mention that I installed Realplayer as per post # 34 for amd64.

---

### Post by ubuntu-freak on 2008-03-01
> **popatopalous said:**
> There are sites like RTE [Ireland] that won't play with any thing except Realplayer. Realplayer is needed for some of us. As far as I can tell it is impossible to get Realplayer to work in Firefox in 64 bit Kubuntu. If any one has please tell me how.

Edit: [http://www.rte.ie/radio/index.html](http://www.rte.ie/radio/index.html)

Edit #2: I forgot to mention that I installed Realplayer as per post # 34 for amd64.

 
Have you emailed them to complain politely? BBC have responded and other users are having good results also.
 
I was incorrect in my old post. Helix is now not able to play any proprietary format. I've added RealPlayer to my how-to, but 64-Bit users have to stick with the MPlayer, Totem or Xine plugins.  
 
Nathan

---

### Post by Reindhardt on 2008-04-19
Thanks DUDE this really worked für Mir!!!

Danke

---

### Post by talking Llama on 2008-05-20
> **Bablefish said:**
> I have a link to an official WIKI that has a link to a download of Real Player.deb file and it still works

[https://help.ubuntu.com/community/RealplayerInstallationMethods](https://help.ubuntu.com/community/RealplayerInstallationMethods)

Awesome, thanks for the link Bublefish, it worked perfectly, except just for reference for anyone else the newest RealPlayer at this time is 11 and the code on the site from the link says its RealPlayer 10, just a small detail you'll have to change. :d Thanks very much though! Worked great.

---

