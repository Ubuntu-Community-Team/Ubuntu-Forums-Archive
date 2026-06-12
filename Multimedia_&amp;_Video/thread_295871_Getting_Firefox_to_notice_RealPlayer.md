---
title: "Getting Firefox to notice RealPlayer"
date: 2006-11-08
forum: Multimedia &amp; Video
---

### Post by onocrotalus on 2006-11-08
Hello, I've installed RealPlayer through Synaptic, and the files nphelix.so and nphelix.xpt are present in /usr/lib/mozilla-firefox/plugins. I've completely removed the mplayer plugins. But when I click on a stream (e.g. BBC news), I get the 'please install missing plugin' stuff. Typing about: plugins in Firefox only gives Flash, Java, and the default/catch-all libnullplugin.so. Can anyone help me make Firefox take notice of RealPlayer? I guess I just have to move/rename a plugin file, but I don't know where/which. All help is really appreciated. Thanks!

---

### Post by madmetal on 2006-11-08
i use MediaPlayerConnectivity extension to choose which streams open with realplayer or vlc etc..

---

### Post by onocrotalus on 2006-11-09
Thanks for replying. I have tried that, but I'd quite like some streams/files to not launch a seperate player window (e.g. BBC news). Anyone's ideas on getting FF to see RealPlayer in about: plugins would be welcome - thanks.

---

### Post by Haxwell on 2006-11-16
Hi.. I stumbled across this page with the same question.. So I know somebody of the hundreds (thousands?) of others has figured something out on this? Even a pointer to some documentation would be cool..

Thanks..

---

### Post by Haxwell on 2006-11-17
Okay.. First of all, I'm not sure this has solved the problem, but I'm just trying to document my process.. I know more than the average man, and what I've read makes sense, so you may want to try it too.. anyway..

I found this page [http://lists.helixcommunity.org/pipermail/player-users/2006-August/000528.html](http://lists.helixcommunity.org/pipermail/player-users/2006-August/000528.html)

You should read it for context. From there it suggested that I needed a few files.. 

$ ls /usr/lib/firefox/plugins/
libunixprintplugin.so
$ ls /.firefox/plugins/
ls: /.firefox/plugins/: No such file or directory
$ ls /.mozilla/plugins/
ls: /.mozilla/plugins/: No such file or directory
$ ls ~/.mozilla/plugins/
flashplayer.xpt  libflashplayer.so  nphelix.so  nphelix.xpt

In case you have no idea what the above means, those are commands I ran at the command prompt. After following what it said in that link I posted earlier, this told me that in the firefox plugin directory I did not have two files that the document said should be there. Then the next two commands were just checking possible places Firefox could have been looking for plugins. Finally the last command shows the two files (nphelix.*) that represent RealPlayer. The document said the symbolic links may be broken.

$ file ~/.mozilla/plugins/nphelix.so
/home/johnathanj/.mozilla/plugins/nphelix.so: symbolic link to `/home/johnathanj/apps/real/mozilla/nphelix.so'

I ran a file command to check out the first file.. file will describe what type a file is. This time, it says its a symbolic link to another file. So I'm now checking whether that other file exists and is in otherwise general good health.

$ ls /home/johnathanj/apps/real/mozilla/nphelix.so
/home/johnathanj/apps/real/mozilla/nphelix.so

Well, a general ls reports the file is present, so thats good. Now we run a file command on it to see what type it is..

$ file /home/johnathanj/apps/real/mozilla/nphelix.so
/home/johnathanj/apps/real/mozilla/nphelix.so: ELF 32-bit LSB shared object, Intel 80386, version 1 (SYSV), not stripped

Truthfully, I have no idea what that means, but it looks official. So to sum up at this point. In the ~/.mozilla/plugins folder I have found the two RealPlayer files that the other document said should be there. The doc suggested that they would be broken symbolic links. So I checked on one of them, nphelix.so. A file command revealed it to be a link to an actual file in the folder where I installed RealPlayer. The next couple commands show me doing the same thing for the other file.

$ file ~/.mozilla/plugins/nphelix.
nphelix.so   nphelix.xpt

$ file ~/.mozilla/plugins/nphelix.xpt
/home/johnathanj/.mozilla/plugins/nphelix.xpt: symbolic link to `/home/johnathanj/apps/real/mozilla/nphelix.xpt'

$ file /home/johnathanj/apps/real/mozilla/nphelix.xpt
/home/johnathanj/apps/real/mozilla/nphelix.xpt: data

$ ls /home/johnathanj/apps/real/mozilla/nphelix.xpt
/home/johnathanj/apps/real/mozilla/nphelix.xpt

So anyway, thats all well and good for the ~/.mozilla folder but it says there should be those same files in /usr/lib/firefox/plugins

$ ls /usr/lib/firefox/plugins/
libunixprintplugin.so

And there's not.. So..

$ cp /home/johnathanj/.mozilla/plugins/nphelix.* /usr/lib/firefox/plugins/
cp: cannot create regular file `/usr/lib/firefox/plugins/nphelix.so': Permission denied
cp: cannot create regular file `/usr/lib/firefox/plugins/nphelix.xpt': Permission denied

Damn it!! Security.. Gotta present the administrator credentials..

$ sudo cp /home/johnathanj/.mozilla/plugins/nphelix.* /usr/lib/firefox/plugins/
Password:

Now I make sure I actually copied those files to where I thought I did..

$ ls /usr/lib/firefox/plugins/
libunixprintplugin.so  nphelix.so  nphelix.xpt

I did more reading after that, but the rest didn't exactly seem helpful, or describe my situation anyway. So what you've just read is not a complete solution. For me, the embedded player still does not play. But I hope the above gets you on your way a litte bit. And if nothing else, you learned what file will do. 

Johnathan James - haxwell

---

### Post by Haxwell on 2006-11-17
Okay, more information. I found this page 

[https://player.helixcommunity.org/2005/help/playerfaq.html#mozTocId185543](https://player.helixcommunity.org/2005/help/playerfaq.html#mozTocId185543)

I would have copied the text here, but it wasn't CC or under the GNU FDL, so I hope that link stays valid. Under the topic "How can I troubleshoot the Mozilla plugin?", I compared my system with each point. In checking number 2, my about:buildconfig read 

gcc version 4.0.3 (Ubuntu 4.0.3-1ubuntu5)

and my about:plugins read

RealPlayer G2 Plug-In Compatible version 0.4.0.622 built with gcc 3.2.0 on Jul 18 2006

So at first, I thought damn! Thats my problem! But I trudged on. I checked and my RealPlayer plugin was the only one registered to play RealPlayer streams. That was good. So I checked my system path.

$ set | grep PATH
PATH=/home/johnathanj/blah/blah:/home/johnathanj/foo/foo

But it didn't point to the file realplay which launches the RealPlayer application. It also didn't point to the mozilla plugins folder with the symbolic links I worked so hard finding earlier. So..

$ sudo vi /etc/profile

and I added entries for the PATH. Its too much to go into what the PATH is, how you change it and all that. Using vi (you gotta learn it. suck it up) Just enter

export PATH=/home/**YOURHOME**/real:/home/**YOURHOME**/.mozilla/plugins:/home/**YOURHOME**/real/plugins:${PATH}

that should work. I think. :) You may have to adjust those paths for where the files are on your machine. In other words, YMMV.

The next step was removing a file:

rm /home/johnathanj/.mozilla/firefox/pluginreg.dat

Then I rebooted.

Then I opened Firefox again, and opened bbcmundo.com. They have an embedded player. When I opened it, it found Realplayer and played without the "Could not find appropriate hxplay or realplay in system path." message.

So its working for me and I hope that helps!

Johnathan James - haxwell

---

### Post by onocrotalus on 2006-11-18
Thanks for that! 

$ ls /usr/lib/firefox/plugins/
flashplayer.xpt    libjavaplugin_oji.so  libnullplugin.so       nphelix.so
libflashplayer.so  libjavaplugin.so      libunixprintplugin.so  nphelix.xpt

So I still have the original problem: nphelix.so and nphelix.xpt are sitting in /usr/lib/firefox/plugins, with root permissions, but don't show up in about: plugins in FF. Can anyone sugest why this might be happening...?

---

### Post by onocrotalus on 2006-11-18
SOLVED! I went through what you said again, and it turns out I had a sort of reverse problem to yours. The nphelix files were in /usr/lib/firefox/plugins, but not in ~/.mozilla/plugins - copying them over cures their puzzling absence from about: plugins. Thanks a lot!

---

### Post by Neilguy on 2007-06-28
Thank you, thank you, thank you soooo muchhhh to Haxwell and onocrotalus for geting the problem as many others, and solving it so simply and wonderfully. it's because of ppl like you that the Linux and Ubuntu community is thriving and growing :popcorn:

---

### Post by adwatkin19 on 2007-07-02
Hi all, i followed what Haxwell said and used this command:

export PATH=/home/**YOURHOME**/real:/home/**YOURHOME**/.mozilla/plugins:/home/**YOURHOME**/real/plugins:${PATH}

and things still werent working for me, so i went into my home directory, and found the realplayer folder:

/home/aw/RealPlayer/

and in there is a file called RealPlay, i double clicked it and chose the option "Run in terminal".

it did a little bit of a setup and then real player opened. i closed it off and opened firefox back up, and hey presto, i had live streaming audio.

hope that helps someone.

Adwatkin19

---

### Post by GoneWithTheWind on 2007-07-02
I just downloaded realplayer.

Went to "home" in terminal.

Typed /home/aw/RealPlayer/ ..... and...... nothing.

john@ubuntu:~$ /home/aw/RealPlayer/
bash: /home/aw/RealPlayer/: No such file or directory
john@ubuntu:~$

---

### Post by adwatkin19 on 2007-07-02
The "aw" bit in there should be changed to your user name which looks to be john

so the command would be: cd /home/john/RealPlayer/

that changes the current directory to your home folder, and finds the "RealPlayer" folder

let me know what happends

adwatkin19

---

### Post by Slammer64 on 2007-07-02
There is also a handy-dandy guide to integrating RealPlayer into Firefox on the Ubuntu Guide. Try that and see if it works? [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_handle_rtsp_.28realmedia.29_protocol_in_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_handle_rtsp_.28realmedia.29_protocol_in_Mozilla_Firefox)

---

### Post by GoneWithTheWind on 2007-07-02
Thanks.  I'm still getting the same thing though.  

john@ubuntu:~$ cd /home/john/RealPlayer/
bash: cd: /home/john/RealPlayer/: No such file or directory

A realplayer bin file is slowing up on desktop but doesn't open.

---

### Post by adwatkin19 on 2007-07-03
No problems 

The file on your desktop Right click it and choose "Properties"

On the window that pops up click on the "Permissions" tab, and look for the little check box at the bottom that says "Allow executing file as program" then click on "Close"

the window will dissapear. 

Next open up terminal by clicking on "Applications" > Accessories > Terminal

at the prompt type: cd ~/Desktop

this changes the viewed folder to be your desktop

next type: ls  (that is an L not an i)

this will list all the files and folders on your desktop, you should see the RealPlayer file there.

next job is to install it

so type: sudo ./ followed by the name of the realplayer file

it will start doing things you follow what it says to do. 

once that has completed close off the terminal .

Click on "Places" > Home Folder

When it loads find the "RealPlay" folder and double click it to go in.

find the file "RealPlay" and double click this

when the option of how to run it appears choose with "Run" or "Run in terminal" it should then load the program and go through some setup program, once complete it should take you to the normal player.

Close the player and open firefox and go and find a website that has real streaming on it and test it out, i usually use [www.bbc.co.uk/radio1](www.bbc.co.uk/radio1) website and choose to listen live online. 

Post back here and let us know how you get on. 

adwatkin19

---

### Post by GoneWithTheWind on 2007-07-14
> **adwatkin19 said:**
> No problems 

The file on your desktop Right click it and choose "Properties"

On the window that pops up click on the "Permissions" tab, and look for the little check box at the bottom that says "Allow executing file as program" then click on "Close"

the window will dissapear.

The only thing similar under permissions was "owner - execute, which I checked.  
hen I clicked the "open" tab, added "terminal" as an application to open realplayer, then closed the window.

> Next open up terminal by clicking on "Applications" > Accessories > Terminal

at the prompt type: cd ~/Desktop

this changes the viewed folder to be your desktop

Nothing happens there.  

john@ubuntu:~$ cd ~/desktop
bash: cd: /home/john/desktop: No such file or directory
john@ubuntu:~$ cd
john@ubuntu:~$ cd /desktop
bash: cd: /desktop: No such file or directory
john@ubuntu:~$ pwd
/home/john
john@ubuntu:~$ cd /
john@ubuntu:/$ cd /desktop
bash: cd: /desktop: No such file or directory
john@ubuntu:/$ cd /home/desktop
bash: cd: /home/desktop: No such file or directory
john@ubuntu:/$ cd /
john@ubuntu:/$ /home/desktop
bash: /home/desktop: No such file or directory
john@ubuntu:/$ cd /home
john@ubuntu:/home$ cd /desktop
bash: cd: /desktop: No such file or directory
john@ubuntu:/home$ cd /desktop
bash: cd: /desktop: No such file or directory

---

### Post by adwatkin19 on 2007-07-15
Right lets just confirm this then, on your desktop you have the RealPlayergold10.bin or something named like that?

is that right?

so right click the file and you should have the following tabs on the pop up window: 
Basic , Emblems, permissions, open with and notes.

Click on "Permissions"

Near the bottom you should see a line that says "Execute [tick box] Allow executing file as a program?

is that right?

adwatkin19

---

### Post by GoneWithTheWind on 2007-07-15
> **adwatkin19 said:**
> Right lets just confirm this then, on your desktop you have the RealPlayergold10.bin or something named like that?

is that right?
Right.

> so right click the file and you should have the following tabs on the pop up window: 
Basic , Emblems, permissions, open with and notes.

Click on "Permissions"

Near the bottom you should see a line that says "Execute [tick box] Allow executing file as a program?

is that right?
There is no line like that at the bottom.  What Permissions has is:

File Owner:  John
File Group:  John

Owner:  Read (checked) - Write (checked) - Execute (checked this)
Group:  Read (checked) - Write (unchecked) - Execute (unchecked)
Others:  Read (checked) - Write (unchecked) - Execute (unchecked)

Special Flags:  
Set user ID (unchecked)
Set group ID (unchecked)
Sticky (unchecked)

Text View:  -rwxr--r-
Number View:  1600744
Last Changed:  Date for yesterday at 6:11 pm

---

### Post by adwatkin19 on 2007-07-16
Ok no problem, i think this is because i am using a newer version of Ubuntu than you, not a problem

ignore the right click bit

click on Applications > Acessories > Terminal

at the terminal type in "cd /"

then type ls (that is an L not an I) and this should list all the folders.

There should be one called home

type cd home/

Ok no problem, i think this is because i am using a newer version of Ubuntu than you, not a problem

ignore the right click bit

click on Applications > Acessories > Terminal

at the terminal type in "cd /"

then type ls (that is an L not an I) and this should list all the folders.

there should be one with your name (from the looks of it "john"

type cd john/

Ok no problem, i think this is because i am using a newer version of Ubuntu than you, not a problem

ignore the right click bit

click on Applications > Acessories > Terminal

at the terminal type in "cd /"

then type ls (that is an L not an I) and this should list all the folders.

there should be one called "Desktop"

then type cd Desktop/

Ok no problem, i think this is because i am using a newer version of Ubuntu than you, not a problem

ignore the right click bit

click on Applications > Acessories > Terminal

at the terminal type in "cd /"

then type ls (that is an L not an I) and this should list all the folders.

there should be a file called: RealPlayer10GOLD.bin

if there is then type:  sudo chmod +x RealPlayer10GOLD.bin

it will ask for your password enter it and then it will return to the normal prompt.

then type: sudo ./RealPlayer10GOLD.bin

and the installation begins

is that right?

adwatkin19

---

