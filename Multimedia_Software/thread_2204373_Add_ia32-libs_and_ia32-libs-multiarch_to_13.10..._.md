---
title: "Add ia32-libs and ia32-libs-multiarch to 13.10...  how does one do that?"
date: 2014-02-08
forum: Multimedia Software
---

### Post by shantiq on 2014-02-08
i wish to install   install ia32-libs  on 13.10 so i can activate hotkeys on Atunes    
unfortunately Oracle has removed license or somesuch in recent times and it is getting difficult to add java it seems

i found this route online

> First a downgrade is required and done with the following: create the 'preferences' file:

sudo leafpad /etc/apt/preferences
and insert the following lines:


Package: *       
Pin: release a=precise*
Pin-Priority: 2012


enter:wq to write the file. Pin-Priority must be greater than 1000.


Then you may downgrade the offending applications with:


sudo apt-get dist-upgrade
Then you may install packages that complained about dependencies, like sudo apt-get install ia32-libs-multiarch, or sudo apt-get install ia32-libs.


Finally, you should remove the file you just created:


sudo rm /etc/apt/preferences
because else no new updates would be found.



but it does no longer work

what is one to do?   any clever tricks people have found?

---

### Post by Erik1984 on 2014-02-08
Do you really need Oracle's Java?

To run Java application you can install ```
openjdk-7-jre
```

ia32-libs does no longer exist in 13.10. [http://askubuntu.com/questions/107230/what-happened-to-the-ia32-libs-package](http://askubuntu.com/questions/107230/what-happened-to-the-ia32-libs-package)

---

### Post by shantiq on 2014-02-08
> [COLOR=#000000]Do you really need Oracle's Java?[/COLOR]



no probably not


i need [COLOR=#000000]ia32-libs [i think]("http://sourceforge.net/p/atunes/discussion/656585/thread/837931f2/#7c97")  but i thought that was Oracle; i may be wrong about that 
[/COLOR]then ia32-libs requires ia32-libs-multiarch is what it says on my terminal



i know it requires [COLOR=#000000]ia32-libs to activate certain functions
[/COLOR]also it here it need java but when i enter it in synaptic it is not seen there so not sure

[ATTACH=CONFIG]250184[/ATTACH]

---

### Post by fdrake on 2014-02-08
might help also to know why you need that library . is to install a program? which one?

---

### Post by Erik1984 on 2014-02-08
That package doesn't exist either in 13.10. If you know the name of a specific 32 bit package you need you can install it as follows:
```
sudo apt-get install packagename:i386
```

---

### Post by shantiq on 2014-02-08
hi again euroman    well you can see i have atunes installed on my synaptic but when i run 

[COLOR=#000000][INDENT]sudo apt-get install atunes:i386
[/INDENT]
[/COLOR]

 i get

```
sudo apt-get install atunes:i386
[sudo] password for shan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package atunes

```

---

### Post by shantiq on 2014-02-08
> **fdrake said:**
> might help also to know why you need that library . is to install a program? which one?


hi fdrake   [COLOR=#000000]i wish to install install ia32-libs on 13.10 **so i can activate hotkeys on Atunes **[/COLOR]

---

### Post by fdrake on 2014-02-08
best think you can  do is to download the source archive and build the software for your own architecture . Download the atunes-3.1.1-bin.tar.gz archive from here [http://sourceforge.net/projects/atunes/files/atunes/aTunes%203.1.1/](http://sourceforge.net/projects/atunes/files/atunes/aTunes%203.1.1/). Extract and build it yourself

---

### Post by shantiq on 2014-02-08
thanks fdrake  but that "[COLOR=#000000] Extract and build it yourself [/COLOR]"for me requires more guidance if you have the time and patience to explain

this [here]("http://sourceforge.net/p/atunes/discussion/656585/thread/837931f2/#7c97") is what i want to achieve

---

### Post by fdrake on 2014-02-08
ok download what i told you from the link
right cick the archive and select extract here
there is not much to built here since its all java
open a terminal and run thefollwing command:
```

cd ~/Downloads/atunes-3.1.1
chmod +x ./aTunes.sh
./aTunes.sh (or just double click to run the file aTune.sh)

```

---

### Post by mc4man on 2014-02-08
what you want is - 
```
sudo apt-get  install openjdk-7-jre:i386
```

---

### Post by shantiq on 2014-02-08
thank you fdrake. easy enough...    but at the end of the operation still no sign of those global hotkeys ....    flummox world ....   must be things i do not understand here   ...  it does look from [this post ]("http://sourceforge.net/p/atunes/discussion/656585/thread/837931f2/#7c97")as if they would be accessible once ia32 are in the picture


ha   and then i saw mc4man's suggestion to install ia32   ```
[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get  install openjdk-7-jre:i386
[/FONT][/COLOR]
which installs

[CODE] icedtea-7-jre-jamvm:i386 libatk-wrapper-java-jni:i386 libatk1.0-0:i386 libavahi-glib1:i386 libbonobo2-0:i386  libcairo2:i386 libcanberra0:i386 libdbus-glib-1-2:i386 libgconf-2-4:i386 libgconf2-4:i386 libgdk-pixbuf2.0-0:i386
  libgnome2-0:i386 libgnomevfs2-0:i386 libgraphite2-3:i386 libgtk2.0-0:i386 libharfbuzz0a:i386 libidl0:i386 libjasper1:i386
  liblcms2-2:i386 libnspr4:i386 libnss3:i386 libnss3-1d:i386 liborbit2:i386 libpango-1.0-0:i386 libpangocairo-1.0-0:i386
  libpangoft2-1.0-0:i386 libpcsclite1:i386 libpixman-1-0:i386 libpopt0:i386 libtdb1:i386 libvorbisfile3:i386
  libxcb-render0:i386 libxcb-shm0:i386 libxtst6:i386 openjdk-7-jre:i386 openjdk-7-jre-headless:i386



```
[/CODE]     and all good!

does that do the same as ia32-libs?

but still no global key option on atunes  ...   ?   ...   so maybe the info [here ]("http://sourceforge.net/p/atunes/discussion/656585/thread/837931f2/#7c97")  is erroneous or i am not sseing it

it says elsewhere option is in preferences/player   ...    but nowt so far

anyway thanx to all for help thus far

---

### Post by mc4man on 2014-02-08
Showed up here after installing openjdk-7-jre:i386 though to test them had to change most of the defaults as they conflict with current unity/compiz ones - screen
Maybe try restarting atunes or even a log out/in

---

### Post by shantiq on 2014-02-09
ok there is a kink here for me at this point on the hotkeys being visible/usable...   i reinstalled atunes ... and loading from [COLOR=#000000][FONT=Ubuntu Mono]./aTunes.sh   i get this message

[/FONT][/COLOR]> OpenJDK 64-Bit Server VM warning: You have loaded library /home/shan/atunes-3.1.1.DONOTDELETE/libJXGrabKey.so which might have disabled stack guard. The VM will try to fix the stack guard now.It's highly recommended that you fix the library with 'execstack -c <libfile>', or link it with '-z noexecstack'.
INFO       2014-02-09 09:02:01,055        No hotkeys supportednull
INFO       2014-02-09 09:02:01,060        Hotkeys are not supported


[COLOR=#000000][FONT=Ubuntu Mono]


i am on 13.10 with Lxde desktop


will have a a further look   ....    any suggestions meantime? how do i fix the library ?  not sure what is required



[/FONT][/COLOR]

---

### Post by shantiq on 2014-02-10
still cannot see what to do here ....
i have 

> [COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get  install openjdk-7-jre:i386[/FONT][/COLOR][COLOR=#000000][B][RIGHT][/RIGHT]
[/B][/COLOR]
 and > [COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get  install openjdk-7-jre




installed and have tried both deb and my own build


still with this message tho


> [/FONT][/COLOR][COLOR=#000000]*OpenJDK 64-Bit Server VM warning: You have loaded library /home/shan/atunes-3.1.1.DONOTDELETE/libJXGrabKey.so which might have disabled stack guard. The VM will try to fix the stack guard now.It's highly recommended that you fix the library with 'execstack -c <libfile>', or link it with '-z noexecstack'.*[/COLOR]
[COLOR=#000000]*INFO 2014-02-09 09:02:01,055 No hotkeys supportednull*[/COLOR]
[COLOR=#000000]*INFO 2014-02-09 09:02:01,060 Hotkeys are not supported*[/COLOR][COLOR=#000000][FONT=Ubuntu Mono]



any ideas?   anyone?   thanx    shan


[/FONT][/COLOR]

---

### Post by monkeybrain20122 on 2014-02-10
Cannot help you but just want to say that this decision to remove ia32-libs is quite unreasonable (is that a Debian decision or a Ubuntu one?) Sure it is an umbrella package and you can install the needed 32 bit libs individually, but it is not always obvious what these libs are.

---

### Post by shantiq on 2014-02-11
well    MB    apparently    this   > [COLOR=#000000][FONT=Ubuntu Mono]*sudo apt-get install openjdk-7-jre:i386*[/FONT][/COLOR]   replaces the old ia32   ;   but in my case i have an additional kink it seems
mc4man   got it going   on his system so i know it can be done   but i cannot seem to  ....     maybe **something else is missing too** on my setup
Any knowledgeable folks among you here might guess what it could be?
PS i have posted on atunes [support]("https://sourceforge.net/p/atunes/bugs/537/")   no comeback as yet

---

### Post by mc4man on 2014-02-11
Don't see why it's not working for you though here I'm on 14.04 Ubuntu
(assume you've tried this .deb & open atunes  from whatever menu  Lxde desktop provides?
[http://sourceforge.net/projects/atunes/files/atunes/aTunes%203.1.1/](http://sourceforge.net/projects/atunes/files/atunes/aTunes%203.1.1/)

---

### Post by shantiq on 2014-02-12
well mc i have used the deb and   3.1.1 and [3.2.0 beta]("https://sourceforge.net/projects/atunes/files/latest-builds/")


and all the same the option does not appear
maybe you have installed something extra in your 32-java-related travels which i still miss   ...   i have no idea what could be missing it gives this message


> [COLOR=#000000][COLOR=#000000]*[I]OpenJDK 64-Bit Server VM warning: You have loaded library /home/shan/atunes-3.1.1.DONOTDELETE/libJXGrabKey.so which might have disabled stack guard. The VM will try to fix the stack guard now.It's highly recommended that you fix the library with 'execstack -c <libfile>', or link it with '-z noexecstack'.*[/I][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]*[I]INFO 2014-02-09 09:02:01,055 No hotkeys supportednull*[/I][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000]*[I]INFO 2014-02-09 09:02:01,060 Hotkeys are not supported*[/I][/COLOR][/COLOR]


which is probably computer gobbledegook     for you are missing something here  :)

---

### Post by dannyboy79 on 2014-02-12
i'm afraid you've messed around so much now that it will be tough to get you straigthened out. you need to remove the installation you performed of the source files or deb you downloaded and installed. We can see by the output that it's using libJXGrabKey.so from your /home/ folder which is causing it to disable stack guard which "could" be related to why you aren't getting options to use hotkeys. 

People need to understand that ia32-libs is gone in 13.10 and it's fairly easy to solve. whatever library is failing, you just have to install the equivalent :i386 package. In this case i believe libJXGrabKey:i386 may have solved your problem but i don't know for certain. Also, if you're using 13.10 and you attempted to install ia32-libs, it should've returned a note that it's not available BUT there's 3 packages that replace it, you need to install those for sure.

So, in order to fix this you need to clean up your system the best you can and remove that extra atunes you installed and just use the atunes from the repositories. Then we can launch it from the terminal and read hte output and determine what i386 library you're missing.

---

### Post by shantiq on 2014-02-12
Thanx for input Dannyboy  
i do not see where i "[COLOR=#000000]messed around so much[/COLOR]"  :)   i was tidy at every step and now have only 3.2.0


anyway 

[http://packages.ubuntu.com/trusty/amd64/libjxgrabkey-jni/download](http://packages.ubuntu.com/trusty/amd64/libjxgrabkey-jni/download)   is required to install
[https://launchpad.net/ubuntu/raring/i386/libjxgrabkey-java/0.3.2-6](https://launchpad.net/ubuntu/raring/i386/libjxgrabkey-java/0.3.2-6)

>>>>

```
 sudo dpkg -i libjxgrabkey-jni_0.3.2-7_amd64.deb
Selecting previously unselected package libjxgrabkey-jni:amd64.
(Reading database ... 338831 files and directories currently installed.)
Unpacking libjxgrabkey-jni:amd64 (from libjxgrabkey-jni_0.3.2-7_amd64.deb) ...
Setting up libjxgrabkey-jni:amd64 (0.3.2-7) ...
shan@shan:~/Desktop$ sudo dpkg -i libjxgrabkey-java_0.3.2-3_all.deb
(Reading database ... 338836 files and directories currently installed.)
Preparing to replace libjxgrabkey-java 0.3.2-3 (using libjxgrabkey-java_0.3.2-3_all.deb) ...
Unpacking replacement libjxgrabkey-java ...
Setting up libjxgrabkey-java (0.3.2-3) ...

```



this is   the full terminal   down to where the hotkeys are NOT loaded


```
cd atunes-3.2.0DONOTDELETE ;  ./aTunes.sh INFO       2014-02-12 21:04:53,439        Java Virtual Machine: 1.7.0_51
INFO       2014-02-12 21:04:53,452        Arguments: []
INFO       2014-02-12 21:04:53,456        Operating System: Linux 3.11.0-17-generic (amd64)
INFO       2014-02-12 21:04:53,456        Build number: 6263
INFO       2014-02-12 21:04:53,456        Debug mode: false
INFO       2014-02-12 21:04:53,456        Version: aTunes 3.2.0  BETA
INFO       2014-02-12 21:04:53,457        Execution path: /home/shan/atunes-3.2.0DONOTDELETE
INFO       2014-02-12 21:04:54,082        Setting language: en
INFO       2014-02-12 21:04:54,419        Reading serialized object: net.sourceforge.atunes.kernel.modules.repository.Repository from file: /home/shan/.atunes/repository.dat
INFO       2014-02-12 21:04:58,185        Reading net.sourceforge.atunes.kernel.modules.repository.Repository done (3.746 seconds)
INFO       2014-02-12 21:04:59,403        Reading serialized object: net.sourceforge.atunes.kernel.modules.favorites.Favorites from file: /home/shan/.atunes/favorites.dat
INFO       2014-02-12 21:04:59,405        /home/shan/.atunes/favorites.dat (No such file or directory)
INFO       2014-02-12 21:04:59,407        Reading net.sourceforge.atunes.kernel.modules.favorites.Favorites done (0.002 seconds)
INFO       2014-02-12 21:04:59,408        Reading serialized object: java.util.ArrayList from file: /home/shan/.atunes/podcastFeeds.dat
INFO       2014-02-12 21:04:59,409        /home/shan/.atunes/podcastFeeds.dat (No such file or directory)
INFO       2014-02-12 21:04:59,409        Reading java.util.ArrayList done (0.0 seconds)
INFO       2014-02-12 21:04:59,410        Reading serialized object: net.sourceforge.atunes.kernel.modules.statistics.Statistics from file: /home/shan/.atunes/statistics.dat
INFO       2014-02-12 21:04:59,479        Reading net.sourceforge.atunes.kernel.modules.statistics.Statistics done (0.065 seconds)
INFO       2014-02-12 21:04:59,480        Reading serialized object: net.sourceforge.atunes.kernel.modules.playlist.ListOfPlayLists from file: /home/shan/.atunes/playLists.dat
INFO       2014-02-12 21:04:59,539        Reading net.sourceforge.atunes.kernel.modules.playlist.ListOfPlayLists done (0.059 seconds)
INFO       2014-02-12 21:06:14,205        List of availables engines : {MPlayer}
INFO       2014-02-12 21:06:14,206        Selected player engine: net.sourceforge.atunes.kernel.modules.player.mplayer.MPlayerEngine@5118c26e
INFO       2014-02-12 21:06:14,747        Start count: 5
INFO       2014-02-12 21:06:14,776        Application started (81.303 seconds)
INFO       2014-02-12 21:06:15,003        Repository will not refresh automatically
INFO       2014-02-12 21:06:17,940        0 audio objects of play lists not found
[COLOR=#800000]OpenJDK 64-Bit Server VM warning: You have loaded library /home/shan/atunes-3.2.0DONOTDELETE/libJXGrabKey.so which might have disabled stack guard. The VM will try to fix the stack guard now.[/COLOR]
[COLOR=#800000]It's highly recommended that you fix the library with 'execstack -c <libfile>', or link it with '-z noexecstack'.[/COLOR]
[COLOR=#800000]INFO       2014-02-12 21:06:18,496        No hotkeys supportednull[/COLOR]
[COLOR=#800000]INFO       2014-02-12 21:06:18,559        Hotkeys are not supported[/COLOR]



```

---

### Post by mc4man on 2014-02-12
It's 13.10, what not sure.
Also the bit about "OpenJDK 64-Bit Server VM warning: ..." may be a red herring & not the actual reason why global key support can't be enabled.
Suffice to say it does work on 14.04 which you should use at some point..

Here's an ex. from 14.04 using a dl'ed 3.2 atunes - 
by default the .so shows this -
> execstack -q  '/home/doug/Downloads/atunes-3.2.0/libJXGrabKey.so' 
[COLOR="#FF0000"]-[/COLOR] /home/doug/Downloads/atunes-3.2.0/libJXGrabKey.so
Which I believe means it's set to not requiring executable stack & there is no warning & global hotkeys work

However if I set it to requiring  - 

> execstack -s '/home/doug/Downloads/atunes-3.2.0/libJXGrabKey.so' 
doug@doug-Lenovo-IdeaPad-Y580:~$ execstack -q '/home/doug/Downloads/atunes-3.2.0/libJXGrabKey.so' 
[COLOR="#FF0000"]X[/COLOR] /home/doug/Downloads/atunes-3.2.0/libJXGrabKey.so

Then I get the warning but global hot keys still work - 
> /home/doug/Downloads/atunes-3.2.0/aTunes.sh
.........
OpenJDK Server VM warning: You have loaded library /home/doug/Downloads/atunes-3.2.0/libJXGrabKey.so which might have disabled stack guard. The VM will try to fix the stack guard now.
It's highly recommended that you fix the library with 'execstack -c <libfile>', or link it with '-z noexecstack'.
INFO       2014-02-12 20:38:31,142        Hotkeys activated successfully



Now in 13.10 you always get the warning & global hotkeys are never enabled irregardless if the .so is marked as requiring or not requiring.

So i'd just put aside until you go to 14.04....

---

### Post by shantiq on 2014-02-13
ya   thanx for that mc;   so to summarize in 14.04 it works whatever you do;  in 13.10 it does not whatever you do .....   hmmmm...    that is why i love computers ::::}}   they really keep you on your toes  ...    i will wait for 14.04   ..... i only have one machine      and i have been burnt before with "early" upgrades    

There has to be a way tho ....    since it must also have worked on earlier versions too   ...    so why should 13.10 be skipped   ....     the question here is what has/does   14.10 do that 13.10 does not in relation to this


Much appreciate input anyhow;   it all is such a puzzle sometimes :)

---

### Post by shantiq on 2014-02-27
so finally


with help from Fleax maintainer of aTunes got there



first


```
sudo apt-get install openjdk-7-jre:i386

```



add this to bottom of  aTunes.sh




> /usr/lib/jvm/java-7-openjdk-i386/jre/bin/java -Dsubstancelaf.windowRoundedCorners=false -Dinsubstantial.looseTableCellRenderers=true -Djava.library.path=./ -Xms128m -Xmx256m -splash:splash.gif -cp aTunes.jar:lib/* net.sourceforge.atunes.Main $args




then edit/preferences/player  enable hotkeys    then probably a message saying clash of keys with existing programs


I suggest as an unlikely clash setup


 [[IMG]http://s20.postimg.org/s62aby6ft/hotkeys_Atunes.jpg[/IMG]]("http://postimg.org/image/s62aby6ft/")

---

### Post by snehalpatel-it on 2014-07-10
Is there anyother way we can istall ia32-libs ?

Becuase i install 64bit Ubuntu 13.04 and i dont have internet at starting level. Becuase i need to access that with cyber-roam. and Cyber-Roam is 32bit i am not able to find 64bit so when i try to install it says that no shuch files or directory. 

So i connected with internet using usb net. I updated with sudo apt-get update and install with sudo apt-get install ia32-libs command.

Than i was able to login with cyberclient.

So if you have any alternative solution without connecting internet to install cyberclient and ia32-libs please let me.

Thanks

---

