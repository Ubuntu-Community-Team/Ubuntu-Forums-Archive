---
title: "Cinelerra installed, but will not run (gutsy)"
date: 2007-11-26
forum: Multimedia Production
---

### Post by Enik Feirgraw on 2007-11-26
I have desperately been trying to install Cinelerra, with very little success. I am quite new to linux in general (I have all of maybe 3 days experience with it now). I finally got Cinelerra to install, but whenever I try to run it, nothing happens.

I am running Gutsy Gibbon
Laptop is a Toshiba Satellite A55
1.4 Gh Celeron
1GB Ram

The repository I used to install Cinelerra is this
deb [http://giss.tv/~vale/ubuntu32](http://giss.tv/~vale/ubuntu32) ./

I installed all the necessary depositories (as far as I know of, since it actually installed finally).

I have tried to compile the source, but I get error messages that I don't have any idea how to fix (I would like to avoid compiliing source if possible, but if not I will be happy to provide the error message)

I searched the forum, and many outside sites for help, but couldn't quite find the help I needed. If anybody has any ideas, or an answer to this problem, I would greatly appreciate it/them.
Thank you to everyone in advance.

---

### Post by Iandefor on 2007-11-26
Try running it from a terminal (Applications->Accessories->Terminal) and posting the output here.

It wouldn't hurt also to post what the error messages you get during compilation are, and where you got the source from. (ie, did you check it out from SVN or did you download a release?)

---

### Post by smithee77 on 2007-11-26
Hello everybody,
I've got similar situation.

I'm running Ubuntu 7.10 in Sony Vaio with Nvidia Geforce 7600.3D acceleration runs ok.

I've installed cinelerra using the repository 

deb [http://giss.tv/~vale/ubuntu32](http://giss.tv/~vale/ubuntu32) ./
deb-src [http://giss.tv/~vale/ubuntu32](http://giss.tv/~vale/ubuntu32) ./

and installation went ok. The problem starts when running cinelerra using Terminal...I got this one:

[I]cinelerra: symbol lookup error: /usr/lib/libguicast.so.1: undefined symbol: glDeleteShader
[/I]

any clue?
Thanks in advance!

---

### Post by Enik Feirgraw on 2007-11-26
When I try to compile, I can olny get to ./configure, upon execution, I recieve this message.

./configure: 11: arch: not found
./configure: 24: arch: not found
[: 24: i686: unexpected operator
[: 31: ==: unexpected operator
./configure: 47: Syntax error: Bad fd number

The source code I downloaded was from heroine virtual.

When I installed Cinelerra via synaptic, the repository I used was
deb [http://giss.tv/~vale/ubuntu32](http://giss.tv/~vale/ubuntu32) ./
Which I had gotten from the CinelerraCV site
[http://cvs.cinelerra.org/getting_cinelerra.php#ubuntu](http://cvs.cinelerra.org/getting_cinelerra.php#ubuntu)

I tried to execute the installed Cinelerra by using the terminal before I had posted this thread, but I was not sure how. I was looking in forums as to what commands would get me to the filesystem (You probably already know this, but it was installed in Filesystem>Usr>Bin). The only answer I found was the command
Sudo su
All this did though, was change everything from
user@computer:~$
To
root@computer:~$
All my listed and accessible directories were still home.
Hopefully I had just found incorrect information, and you could properly tell me how to access the filesystem through the terminal.

Thanks for the continued assistance.

---

### Post by Iandefor on 2007-11-27
> **Enik Feirgraw said:**
> When I installed Cinelerra via synaptic, the repository I used was
deb [http://giss.tv/~vale/ubuntu32]("http://giss.tv/%7Evale/ubuntu32") ./
Which I had gotten from the CinelerraCV site
[http://cvs.cinelerra.org/getting_cinelerra.php#ubuntu](http://cvs.cinelerra.org/getting_cinelerra.php#ubuntu)

I tried to execute the installed Cinelerra by using the terminal before I had posted this thread, but I was not sure how. I was looking in forums as to what commands would get me to the filesystem (You probably already know this, but it was installed in Filesystem>Usr>Bin). The only answer I found was the command
Sudo su
All this did though, was change everything from
user@computer:~$
To
root@computer:~$
All my listed and accessible directories were still home.
Hopefully I had just found incorrect information, and you could properly tell me how to access the filesystem through the terminal.

Thanks for the continued assistance.When you open up the terminal, you're already accessing the filesystem. The prompt you see when you open it up (**ian@leviathan:~$** on my machine) is actually composed of three parts: your user name (**ian**), the name of the machine you're using (in this case, it's called **leviathan**), and then what's known as your **working directory**. It shows up as a **~** in my example because that's a shortcut that means "the current user's home directory". If I change my working directory (done with **cd [wherever I want to go]**) to, say /etc/fonts, my prompt now reads** ian@leviathan:/etc/fonts$** 

The binary you want is just called 'cinelerra' and it's in /usr/bin. You should be able to just open up the terminal and run 'cinelerra' (without the quotes).

Linux systems usually have a list of directories (called a path) to look through when you enter a command; if it finds the corresponding command, it runs it. In this case, cinelerra should just run when you enter it (from anywhere on the filesystem) because it's in a directory that's a part of the path.

By the way, I'd recommend [reading up on sudo]("https://help.ubuntu.com/community/RootSudo") (since you seem to have come across it) if you don't already know what it is. Another useful document to start with, if you want to learn more about using the terminal would be [Using The Terminal]("https://help.ubuntu.com/community/UsingTheTerminal?action=show&redirect=Terminal") from the Ubuntu Documentation.
> When I try to compile, I can olny get to ./configure, upon execution, I recieve this message.

./configure: 11: arch: not found
./configure: 24: arch: not found
[: 24: i686: unexpected operator
[: 31: ==: unexpected operator
./configure: 47: Syntax error: Bad fd numberInteresting. It sounds like the configure script that they supplied is broken. I'm downloading the source from Heroine Virtual right now to take a look.

EDIT: I've found two things that prevent ./configure from running successfully. There are more, but I'm tired and I need sleep.

The first is that the first line is **#!/bin/sh**, which, on any other distro, would be perfectly reasonable. For reasons I'm not going to get into here, [that won't work for this particular script on Ubuntu]("https://wiki.ubuntu.com/DashAsBinSh"). Change that line to **#!/bin/bash**. 

For more information about that first line, [see Wikipedia]("http://en.wikipedia.org/wiki/Shebang_%28Unix%29").

The next step: There are two references to `arch`, which doesn't exist on Ubuntu. The following command will strip out any references to the command and replace them with one that (based on what I can see) should be functionally equivalent to arch. Run it in the same directory as the configure script is in:
> sed -i 's/arch/uname \-m/g' configureFor reference, there are simpler ways to do that, but I'm tired and that command does the trick.

And, finally, make sure you install the packages **nasm** and **yasm** before running configure again.

---

### Post by Enik Feirgraw on 2007-11-27
Well, I tried to run cinelerra from the terminal, and still no luck. This time (thanks to you) I was able to produce some sort of result. As of current, when I run the synaptic installed cinelerra, I get this message:

[B]enik@Neflheim:~$ cinelerra
cinelerra: symbol lookup error: /usr/lib/libquicktimehv-1.6.0.so.1: undefined symbol: faacDecOpen.[/B]

I have libquicktimehv-1.6.0.so.1 in my libraries, so I am not sure of the problem. I don't know if this has anything to do with the problem, but I also have libquicktimehv-1.6.0.so.1.0.0 in the libraries as well.
I am hoping there is some sort of fairly easy fix for this problem (or just a fix alltogether, because I get the feeling that compiling the source would have the same issues, but that is just a feeling, I really wouldn't know for a fact)

As for the source code... I went into the configure script, and changed the #!/bin/sh to #!/bin/bash.
I tried the command you gave me afterwards, and still nothing. I might have misunderstood something with the command, but I did try it several times and several ways. Here are the results:

[B]enik@Neflheim:~/cinelerra-2.1$ sed -i's/arch/uname \-m/g'configure
Usage: sed [OPTION]... {script-only-if-no-other-script} [input-file]...

  -n, --quiet, --silent
                 suppress automatic printing of pattern space
  -e script, --expression=script
                 add the script to the commands to be executed
  -f script-file, --file=script-file
                 add the contents of script-file to the commands to be executed
  -i[SUFFIX], --in-place[=SUFFIX]
                 edit files in place (makes backup if extension supplied)
  -l N, --line-length=N
                 specify the desired line-wrap length for the `l' command
  --posix
                 disable all GNU extensions.
  -r, --regexp-extended
                 use extended regular expressions in the script.
  -s, --separate
                 consider files as separate rather than as a single continuous
                 long stream.
  -u, --unbuffered
                 load minimal amounts of data from the input files and flush
                 the output buffers more often
      --help     display this help and exit
      --version  output version information and exit

If no -e, --expression, -f, or --file option is given, then the first
non-option argument is taken as the sed script to interpret.  All
remaining arguments are names of input files; if no input files are
specified, then the standard input is read.

E-mail bug reports to: [email]bonzini@gnu.org[/email] .
Be sure to include the word ``sed'' somewhere in the ``Subject:''  field.
[/B]

Suspecting user error, I copied and pasted the command as you typed it, and found out I was missing a couple of spaces I did not see:

[B]enik@Neflheim:~/cinelerra-2.1$ sed -i' s/arch/uname \-m/g' configure
sed: no input files[/B]

Suspecting that maybe "uname" was in reference to my username, I tried replacing uname with enik, still no luck:
[B]enik@Neflheim:~/cinelerra-2.1$ sed -i' s/arch/enik \-m/g' configure
sed: no input files[/B]

I double checked to make sure that the configure script was exactly named as configure, in case that might have been the trouble. The script had the exact name, so there is nothing wrong with the command in file reference, as I can tell. I have a slight feeling however, that I might have made an error with the command, because I see no other reason as to why it wouldn't work.

Things did change a little bit though. When I run ./cofigure now, the error message has changed slightly:
[B]enik@Neflheim:~/cinelerra-2.1$ ./configure
./configure: line 11: arch: command not found
./configure: line 14: arch: command not found
./configure: line 14: [: ==: unary operator expected
 *** GCC 3.2.2 or greater is required.  Download it from gcc.gnu.org
Giving up and going to a movie.
[/B]

I have GCC 4.2 (I believe that is the version, nonetheless my version is newer than 3.2.2), and I installed GCC 3.3 in case there were some issues with backwards compatibility. Still no luck.

I do have both yasm, and nasm installed. Before I posted this thread, I had installed them, believing that their absence was the sole source to my troubles.

I hope all this information helps you to help me get this working. Thank you so very much fo your patience and your help, I greatly appreciate it. Also, thank you for the reading material, it is helping me understand a little more about what is going on.

---

### Post by Iandefor on 2007-11-28
Hold on, I've got cinelerra to compile and run (I was running into the same error you got when trying.to run it).

I used the following two sources to get it working:

[http://ubuntuforums.org/showthread.php?t=583060](http://ubuntuforums.org/showthread.php?t=583060)
[http://www.unixadmintalk.com/f59/mplayer-error-undefined-symbol-faacdecopen-137960/#post479357](http://www.unixadmintalk.com/f59/mplayer-error-undefined-symbol-faacdecopen-137960/#post479357)

For a more step-by-step process, read on.

I checked out source from Subversion with the following command (you need the package **subversion** for this to work):```
svn checkout svn://svn.skolelinux.org/cinelerra/trunk/hvirtual
```The source from Subversion actually works with Ubuntu.

Cinelerra has a lot of build dependencies. You can install them with the following command (Copy and paste is your friend): ```
sudo apt-get install g++ git-core cogito subversion automake libtool nasm x11proto-xf86vidmode-dev libxv-dev libxxf86vm-dev libogg-dev libvorbis-dev libtheora-dev libopenexr-dev libdv-dev libpng12-dev libjpeg62-dev libtiff4-dev libfreetype6-dev libsndfile1-dev uuid-dev libasound2-dev libavutil-dev libmpeg3-dev libavcodec-dev libx264-dev libfaac-dev libmjpegtools-dev fftw3 fftw3-dev liba52-0.7.4-dev liblame-dev libfaad2-dev libesd0-dev libiec61883-dev libavc1394-dev
``` Once those are installed, enter the cinelerra source directory and run **'./autogen.sh' **(without quotes). Normally, sources that include autogen.sh are set up to run configure automatically from autogen.sh. Not so with cinelerra; just run **./configure** after ./autogen.sh. Then run the command **make** and, if no errors occur, then **sudo make install**.

Normally, that would be the end of the instructions, but, after successfully compiling and installing cinelerra, I found that two extra steps were needed: reinstalling faad and libfaad2-0:
```
sudo apt-get --purge remove faad libfaad2-0
```At this point, apt may want to remove a number of other packages. Feel free to remove them as long as you note them down (copy + paste is your friend, again) and remember to reinstall them again later. Now, run ```
sudo apt-get install faad libfaad2-0
```Finally, cinelerra seems to have a problem with a particular value the kernel uses and the recommended fix is to run the following as root (you can start up what is effectively a root terminal with **sudo -s**).```

echo "0x7fffffff" >/proc/sys/kernel/shmmax
```For more information about the /proc filesystem (really quite useful information if you're going to be using Linux, even if you never practically use it), [Red Hat]("http://www.redhat.com/docs/manuals/linux/RHL-7.2-Manual/ref-guide/ch-proc.html") has some good documentation up about it. Once you're familiar with /proc, you may want to learn about [/sys]("http://wiki.linuxquestions.org/wiki/Sysfs_file_system") (which is intended to eventually replace /proc).

---

### Post by smithee77 on 2007-11-29
Perfect!
Runs great. Many thanks for your help.

I will add a detail. If you reboot your system the change
*echo "0x7fffffff" >/proc/sys/kernel/shmmax*
gets lost. To keep it forever just:

1.*sudo gedit /etc/sysctl.conf*
2.Add at the end of the file
*kernel.shmmax=0x7fffffff*

---

### Post by Enik Feirgraw on 2007-11-30
Hey, thanks for all the help Iandefor. Unfortunatley, more has gone wrong and Cinelerra is still not working. I am extremely tired right now, so I am not going to post the code, but I can still tell you what is going wrong, and I could post the code later. (I would post the code right now, but the computer with Ubuntu is shut off at th moment.)

When I get to the second step in your walkthrough, issuing the command should install all the dependencies for cinelerra, as I understand. Well, it does what it can, then it will say that it cannot find one of the files. I figured something went wrong, so I went on a search for the files manually. Found them, and began installing them. They had their own dependencies, no problem, installed those as well. After Getting two of the files working (the terminal would only list one, and then I would have to run the command again to find out which file it could not find next), I came to one that would NOT install (something about a broken pipe. I will post the code tomorrow, since it will be the weekend and I wont have to worry about getting up for school). Libmjpegtools-dev required libmjpegtools0, which caused a "broken pipeline" when it was trying to install. Something along those lines anyway. I will give you a more accurate account of what is going on over the weekend, but again, now I am tired and have a headache, and have to be ready for school soon, so everything is sketchy and rough.

So, in short, I am not able to get past step 2 (yes, I copy and pasted all the code you gave me.). I REALLY want to get cinelerra working, so please bare with me on this. Again, thank you so much for all the help, you have no idea how much I appreciate it. On the bright side, at least it was has been an educations experience for me.

---

### Post by aAnaRchY on 2007-11-30
I am not able to get past step 2.  This is what i get: 
[B]The following packages have unmet dependencies:
  libfaac-dev: Depends: libfaac0 (= 1.24clean-0ubuntu4) but 1.25-0.1~3v1ubuntu0 is to be installed
E: Broken packages[/B]](*,)

This is the same error that i get if i install the deb package of cinelerra!](*,)

---

### Post by thefriend on 2007-11-30
well just today ther is a new directory on giss.tv

I added deb [http://giss.tv/~vale/ubuntuopengl](http://giss.tv/~vale/ubuntuopengl) ./
and it worked for me on a gutsy ubuntu.

have fun 

Andy

[Edit: with this cinelerra i cannot import mov files - it crashes without notice :(]

---

### Post by aAnaRchY on 2007-11-30
> **thefriend said:**
> well just today ther is a new directory on giss.tv

I added deb [http://giss.tv/~vale/ubuntuopengl](http://giss.tv/~vale/ubuntuopengl) ./
and it worked for me on a gutsy ubuntu.

have fun 

Andy

[Edit: with this cinelerra i cannot import mov files - it crashes without notice :(]

Thanks!:guitar:That worked great!

---

### Post by Enik Feirgraw on 2007-12-01
> **thefriend said:**
> well just today ther is a new directory on giss.tv

I added deb [http://giss.tv/~vale/ubuntuopengl](http://giss.tv/~vale/ubuntuopengl) ./
and it worked for me on a gutsy ubuntu.

have fun 

Andy

[Edit: with this cinelerra i cannot import mov files - it crashes without notice :(]

Good news and bad news.
Bad news: The link quoted did not work for me, still had some major problems I hope it is able to help others though, as it already has. Thanks for the help thefriend
Good News: I finally found was able to get Cinelerra working on my computer. I followed Inadefor's walkthrough mostly (with the additions of what smithee77 added). The second step in the walkthrough would not work for some reason. I skipped the step entirely for my gutsy, and just headed onto the third step. By skipping the second step, Cinelerra installed, and now runs. My deepest gratitude goes to Iandefor for all the help and patient he gave.

Now, I just have a few final questions...
What formats does Cinelerra support for input video? I can't seem to get anything to play (mostly concerned about AVI).
If no way to support video formats other than MOV, how would I convert videos to MOV in Ubuntu? (Terminal? GUI converter?)
Edit: When I try to load MOV files in Cinelerra, it will only load the audio... I will be looking into this, unless somebody has some advice before I figure it out.

And most importantly, (the first two questions have little relevance to the thread topic, but I would appreciate and answer or link please) do I mark this thread as solved now?

---

### Post by Unterseeboot_234 on 2007-12-01
I had Cinelerra working. And I had a new update this morning that worked. However, when I tried to configure my nVidia card, all Heck broke loose. Cinelerra will not load because it says:

```
cinelerra: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
```

That, and now my restricted driver for nVidia will not load, which is important, evidentially Cinelerra needs the 3d graphics accelerators. I will figure it out. I had it running and I want it back.

===========

Cinelerra is a great program. You will find Kino to be your friend. In fact, load up Kdenlive and Avedumux also. You need all the tools. 

Cinelerra works best in DV file clips (RAW). The codec most of the time is based upon the sound track. AVI will give you problems because of all the gazillion compression schemes from the M$ environment that claim a film clip is .avi but the compression is totally weird.

If you can't load QuickTime clips into Cinelerra, it is either because you dont' have quicktime4linux or your clip your're trying to use has a compression.

Cinelerra has so many option settings. You will need to read up on video formats. Your fastest path to learning Cinelerra is IRC chat, channel #cinelerra on freenode. There users will point you to the gazillion docs, tuts and howtos out there on the web.

================
I found Ubuntu cuts off some of the menu's in Cinelerra -- because Cinelerra does not use the guidelines to make GNOME softwarre and that's why I have a couple of broken links now. I can't config my graphics card, I can't run cinelerra.

---

### Post by chatuu on 2007-12-01
i got the same problem as you =/


if i want to instal libmesa blabla..... it ask for remove nvidia-gls  =/

but i need my nvidia driver;;; so ... what can we do to run  cinelerra ?


libgls.so.1.2  sux

---

### Post by Amstell on 2007-12-01
landefor 

Beautiful Thanks.  Workings perfect.

---

### Post by grantwfuller on 2007-12-02
I am completely new to installing software in Ubuntu but I got as far as getting these files in.
For Ubuntu 7.10 Gutsy Gibbon:

    * for i386, by Valentina MESSERI:

cinelerra_2.1.0-2svn..> 30-Nov-2007 20:51   11M  
  
[   ] libguicast_2.1.0-2sv..> 30-Nov-2007 20:51  385K  
[   ] libmpeg3hv-dev_2.1.0..> 30-Nov-2007 20:51   11K  
[   ] libmpeg3hv_2.1.0-2sv..> 30-Nov-2007 20:51  138K  
[   ] libquicktimehv-dev_2..> 30-Nov-2007 20:53   23K  
[   ] libquicktimehv_2.1.0..> 30-Nov-2007 20:53  2.0M  

The result is, I have a shortcut launcher in the drop down menu but when I double click it flashes a window for a hundredth  of a second and then nothing. The result of trying to launch from the terminal gives this
:
Cinelerra is free software, covered by the GNU General Public License,
and you are welcome to change it and/or distribute copies of it under
certain conditions. There is absolutely no warranty for Cinelerra.
**Illegal instruction (core dumped)**
grant@grant-desktop:~$ 

Am I missing any files? compiling entirely from source code, well, I paint pictures for a living, so I need the simplest solution available. Any help is really welcome.

---

### Post by starcannon on 2007-12-02
TheFriend, thanks that worked for me, first run Cinelerra complained, but its complaint box told me to cli me@my-desktop:~$ sudo echo "0x7fffffff" > /proc/sys/kernel/shmmax
sudo didn't work but sudo bash then that command did, works perfectly.

```
me@my-desktop:~$ sudo bash
root@my-desktop~:$  echo "0x7fffffff" > /proc/sys/kernel/shmmax
```

Thanks again.

---

### Post by tubunu on 2007-12-02
To all the people who got Cinelerra to run on their systems, was it the latest version 2.1 or the previous one (which was a little buggy, imo)?

---

### Post by grantwfuller on 2007-12-02
does anyone know what it means? "Illegal instruction - core dumped"

---

### Post by Iandefor on 2007-12-03
> **Enik Feirgraw said:**
> Good news and bad news.
Bad news: The link quoted did not work for me, still had some major problems I hope it is able to help others though, as it already has. Thanks for the help thefriend
Good News: I finally found was able to get Cinelerra working on my computer. I followed Inadefor's walkthrough mostly (with the additions of what smithee77 added). The second step in the walkthrough would not work for some reason. I skipped the step entirely for my gutsy, and just headed onto the third step. By skipping the second step, Cinelerra installed, and now runs. My deepest gratitude goes to Iandefor for all the help and patient he gave.I'm glad it worked for you eventually. I'm still trying to work out why those exact steps worked for me but not for you. What repositories do you have enabled?

By the way, I've read your other questions but will reserve researching and answering for another day (probably tomorrow). In the meantime, what codecs are you using in the avi's?

---

### Post by Enik Feirgraw on 2007-12-03
> **Iandefor said:**
> I'm glad it worked for you eventually. I'm still trying to work out why those exact steps worked for me but not for you. What repositories do you have enabled?

By the way, I've read your other questions but will reserve researching and answering for another day (probably tomorrow). In the meantime, what codecs are you using in the avi's?

Well, I am fairly certain I am missing a lot of the dependencies. The second step simply didn't work because I couldn't install the dependencies for one reason or another (Some of them, because I couldn't install their own dependencies). I tried to manually install some of the dependencies, but I was only able to get two of them installed before I ran into a brick wall (the third one, It would not install, even though I had all of it's dependencies, and I could not find it on the repositories). Doing the third and forth steps however did the trick in getting it to run.
I should be doing some more research on using Cinelerra, and what it is capable of. I just have a lot I am busy with lately, so things are progressing slowly. Unterseeboot_234 told me a little about Cinelerra and video codecs (as you could see from the post), and suggested the IRC
I believe most of the video codecs I have are gstreamer, along with some random others (probably not so good to mix in random codecs I have no idea about :( )

---

### Post by Iandefor on 2007-12-03
> **chatuu said:**
> i got the same problem as you =/


if i want to instal libmesa blabla..... it ask for remove nvidia-gls  =/

but i need my nvidia driver;;; so ... what can we do to run  cinelerra ?

libgls.so.1.2  sux Is it asking for libGL.so.1.2? If so, try the following command:
```
sudo ln -s /usr/lib/libGL.so.1 /usr/lib/libGL.so.1.2
```That makes a softlink (A file which just points to another file) to the libGL already on your system. It should work after that.> **grantwfuller said:**
> I am completely new to installing software in Ubuntu but I got as far as getting these files in.
For Ubuntu 7.10 Gutsy Gibbon:

    * for i386, by Valentina MESSERI:

cinelerra_2.1.0-2svn..> 30-Nov-2007 20:51   11M  
  
[   ] libguicast_2.1.0-2sv..> 30-Nov-2007 20:51  385K  
[   ] libmpeg3hv-dev_2.1.0..> 30-Nov-2007 20:51   11K  
[   ] libmpeg3hv_2.1.0-2sv..> 30-Nov-2007 20:51  138K  
[   ] libquicktimehv-dev_2..> 30-Nov-2007 20:53   23K  
[   ] libquicktimehv_2.1.0..> 30-Nov-2007 20:53  2.0M  

The result is, I have a shortcut launcher in the drop down menu but when I double click it flashes a window for a hundredth  of a second and then nothing. The result of trying to launch from the terminal gives this
:
Cinelerra is free software, covered by the GNU General Public License,
and you are welcome to change it and/or distribute copies of it under
certain conditions. There is absolutely no warranty for Cinelerra.
**Illegal instruction (core dumped)**
grant@grant-desktop:~$ 

Am I missing any files? compiling entirely from source code, well, I paint pictures for a living, so I need the simplest solution available. Any help is really welcome.That's a known problem with Messeri's packages on AMD processors. What processor are you using? If you don't know, can you paste the output of  **cat /proc/cpuinfo **for me?

> **Enik Feirgraw said:**
> Well, I am fairly certain I am missing a lot of the dependencies. The second step simply didn't work because I couldn't install the dependencies for one reason or another (Some of them, because I couldn't install their own dependencies). I tried to manually install some of the dependencies, but I was only able to get two of them installed before I ran into a brick wall (the third one, It would not install, even though I had all of it's dependencies, and I could not find it on the repositories). Doing the third and forth steps however did the trick in getting it to run.
I should be doing some more research on using Cinelerra, and what it is capable of. I just have a lot I am busy with lately, so things are progressing slowly. Unterseeboot_234 told me a little about Cinelerra and video codecs (as you could see from the post), and suggested the IRC
I believe most of the video codecs I have are gstreamer, along with some random others (probably not so good to mix in random codecs I have no idea about :( )I don't think having random codecs will necessarily hurt unless they're in conflict- which I don't think is likely.

In terms of general Cinelerra usage, the Heroine Virtual website has some [fairly extensive documentation]("http://www.heroinewarrior.com/cinelerra/cinelerra.html").

In terms of codecs, I can't really help you aside from recommending you convert to DV first. It seems to like DV. I'm trying some other options at the moment, but need to wait for the encode to finish- the smallest video file I have is a couple of hundred megabytes large.

---

### Post by cotcot on 2007-12-04
I wrote a howto in [[COLOR="Red"]this[/COLOR]]("http://ubuntuforums.org/showthread.php?t=586370")  thread on how to compile cinelerra in gutsy. 
Read carefully the output of ./configure for the dependencies.
It is important to have it compiled with OpenGL. This improves a lot the real time rendering when you are compositing.

Question to the first poster : is the laptop fast enough to run cinelerra ?

---

### Post by ubstudiorocks on 2007-12-06
Hi landefor, I am also having trouble with the core dumped error, I ran the command like you suggested and this is what I got:

root@AMubstudio:/home/ubstudio# cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 11
model name      : Intel(R) Celeron(TM) CPU                1100MHz
stepping        : 1
cpu MHz         : 1102.531
cache size      : 256 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr sse up
bogomips        : 2205.58
clflush size    : 32

I tried cinelerra on fedora with exactly the same hardware and it worked fine, but I don't want to use fedora.

---

### Post by ugm6hr on 2007-12-08
> **Enik Feirgraw said:**
> I finally got Cinelerra to install, but whenever I try to run it, nothing happens.


I have installed the same way - and have the same problem.  When run from Terminal - I get:

```
cinelerra: symbol lookup error: /usr/lib/libguicast.so.1: undefined symbol: glDeleteShader

```

Anyone know what this means?

---

