---
title: "How to install rtorrent+rutorrent on debian+apache2/PHP"
date: 2011-10-26
forum: Networking &amp; Wireless
---

### Post by Pithikos on 2011-10-26
[FONT=Arial Black][SIZE=2]Intro of darkness, then [COLOR=Black]redness[/COLOR], then [COLOR=Black]whiteness [/COLOR][/SIZE][/FONT]8-)

*26/October/2011*



It took me some hours to install rtorrent and rutorrent on an already web-server so I thought of making a small tutorial to save others some time. We assume that you already have Debian installed and Apache with PHP. The tutorial will probably even work for Ubuntu as it is a Debian-derived distro.

_INDEX_

[LIST=1]
[*]Apache2 configuration
[*]rutorrent Installation
[*]rtorrent Compilation/Installation
[LIST=1]
[*]Compiling and installing xmlrpc-c
[*]Compiling and installing libtorrent
[*]Compiling and installing rtorrent
[/LIST]
 
[*]Running rtorrent as a daemon  (extra)
[*]Autostart rtorrent on boot                (extra)
[/LIST]
 

[COLOR=Red]**ATTENTION**[/COLOR]: To use rutorrent properly you _**MUST**_ compile rtorrent yourself. Else it might still work but you will get all sort of weird behaviour(wrong numbers displayed etc). I talk from experience ;)

____________________________________________________________________________________




**[FONT=Arial Black][SIZE=2]1. Apache2 Configuration[/SIZE][/FONT]**

 To check if you have apache2 run:

```
sudo apache2 -v
```if you get anything at all showing the  version of apache then you indeed have it installed. If not use one of  the 1000 tutorials out there to install **apache and php**. Both are necessary for rutorrent to work.

In order to use r[FONT=Arial]uttoren[/FONT]t we need to install a module called SCGI for Apache2.
```
sudo apt-get install libapache2-mod-scgi
```[FONT=Arial]In order to use the module we have to tell apache to use it. For this we will add two lines to the apache's [/FONT]
[FONT=Arial] configuration file:[/FONT]
```
sudo vi /etc/apache2/apache2.conf
```[FONT=Arial] To edit the configuration file with text editor *vi*. The reason we use *vi* is that it is present on ALL unixes. [/FONT]
[FONT=Arial] You can replace *vi* with *nano*, *gedit*, *geany* or whatever suits you. These are the command lines that you [/FONT]
[FONT=Arial] should add at the end of the file:[/FONT]

```
# rutorrent
LoadModule scgi_module /usr/lib/apache2/modules/mod_scgi.so
SCGIMount /RPC2 127.0.0.1:5000
```The first line is a comment to keep track of what is loaded for what reason. The second line makes sure we load the module. The third line is so that we mount the module. To test if things work properly do:

```
sudo service apache2 restart
```If for some reason you get an error line like "*could not find scgi.so*" then just do:

```
sudo find / -iname "*scgi*so"
```This will search it for you on the whole root filesystem. You will endly(hopefully) get the full path of where scgi module is located(can be different for different versions of apache and scgi). Replace the path in the second line I provided earlier to match the actual path of your scgi module. Save and retest. We assume that apache2 loads correctly now.




**[FONT=Arial Black][SIZE=2]2. rutorrent Installation[/SIZE][/FONT]**

Rutorrent installation is quite straighforward. Rutorrent is a web page package of php and javascript components. Therefore we will just install it where our webpages are. Navigate to

```
cd /var/www
```We are assuming that you have write access to this folder. If not, put a *sudo* infront of the following commands. We get the rutorrent package:

```
wget http://rutorrent.googlecode.com/files/rutorrent-3.3.tar.gz
```You should first check [here]("http://code.google.com/p/rutorrent/downloads/list") if there is a newer version and use that instead. Its format should look like *rutorrent-***.tar.gz* where the asterisk is the version of rutorrent. There are many plugins in there so be careful what you choose.

Once we got the package we untar it:
```

tar -xvzf rutorrent-*
```Remove the package to have things clean and tighty:
```

rm rutorrent*.gz
```Rutorrent is installed. Make sure that you give write/execute access to rutorrent:

```
sudo chmod -R 777 rutorrent
```this will set rutorrent and all subfolders to read/write/execute for everyone. For a multiuser system where many log in and out this is risky. If you are not going to add any torrents via rutorrent then you probably don't need write access but only execute/read(755).
To test the system we navigate to [http://192.168.1.x/rutorrent/](http://192.168.1.x/rutorrent/) to check it out. Voila!!
If you see a circle just going right-round spinning right-round baby right-round then you should make sure _**Javascript is enabled**_. If you get the web interface but with a bunch of errors then you have installed rutorrent succesfully.

Last but not least we have to configure rutorrent so that it uses the right port and IP. Edit the rutorrent configuration file with
```
vim /var/www/rutorrent/conf/config.php
```You only have to care about two values, namely
```
$scgi_port = 5000;
$scgi_host = "127.0.0.1";
```Make sure the port and IP match the port and IP with the last line we added to the apache configuration file earlier.
     



**[FONT=Arial Black][SIZE=2]3. rtorrent  Compilation/Installation[/SIZE][/FONT]**

Now it's time for the kinky stuff! :biggrin:
Go to an empty folder anywhere where you have write access. We are going to use the folder as a temp folder to compile rtorrent and do all these nasty things so to keep things simple and clean use an empty folder.

**[COLOR=Red]ATTENTION[/COLOR]**: If you have installed rtorrent previously from the repositories then run ```
sudo apt-get remove rtorrent
``` to get rid of it. Any configuration files remained will work with the new install.

We have to make sure that these libraries and tools are available in our system

[LIST]
[*]gcc (tool)
[*]ncurses (lib)
[*]libsigc++-2.0 (lib)
[*]libssl (lib)
[*]subversion (tool)
[*]xmlrpc-c (lib)
[/LIST]
You can install the first five with

```
sudo apt-get install gcc ncurses libncurses?-dev libsigc++-2.0-dev libssl-dev subversion
```[SIZE=1]
[/SIZE][INDENT]**[SIZE=1]3.1. Compiling and installing xmlrpc-c[/SIZE]**

For xmlrpc-c we are going to install it in the nasty way. The reason we installed subversion is just so we can get the latest xmlrpc-c from the sources. Subversion is something like the git tool. Just type this to get the latest package using the subversion tool

```
svn checkout http://xmlrpc-c.svn.sourceforge.net/svnroot/xmlrpc-c/advanced xmlrpc-c
```Once you downloaded everything

```
cd x*
```to get into the folder. Then we compile as this:

```
./configure
make
install
```On success we go to the previous folder and remove the package and folder where we untared with
```
cd ..
rm -Rf x*
```-R for recursive and -f to not get any questions.


**[SIZE=1][FONT=Arial]3.2. Compiling and installing libtorrent[/FONT][/SIZE]**

Libtorrent is the library that is being used by rtorrent to use torrents. The latest version as of today(26/oct/2011) is 0.12.9. To download it, type

```
wget http://libtorrent.rakshasa.no/downloads/libtorrent-0.12.9.tar.gz
```You can check [here]("http://libtorrent.rakshasa.no/downloads") if there is a newer version and use that instead. Pay attention to that 0.12- is newer than 0.4-. I did the mistake of installing the latter believing it was newer just because it was showing higher up the list.

Once you got the package untar it with
```

tar -xvzf lib*
```Get in it:
```

 cd lib*
```And now we will compile and install it:
```
./configure
make
install
```That's it!!

Clean up all the mess you did with:
```
cd ..
rm -Rf lib*
```


[SIZE=1] **3.3. Compiling and installing rtorrent**[/SIZE]

Now it's time to get rtorrent(FINALLY!). Just type this to fetch it from the web:

```
wget http://libtorrent.rakshasa.no/downloads/rtorrent-0.8.9.tar.gz
```As of today(26/Oct/2011) 0.8.9 is the latest rtorrent. You would maybe want to check if there is a newer version by going [here]("http://libtorrent.rakshasa.no/downloads/"). Search for the package with name rtorrent-*.tar.gz where the asterisk corresponds to the version of rtorrent.

Once you got the package we will untar it:
```

 tar -xvzf rtorrent-*
```Navigate to the directory with
```
cd rtorrent-*
```Now you have to be **extra careful** on what you type. Type the following to configure rtorrent so that it will use the xmlrpc-c library later on when we compile:
```
./configure --with-xmlrpc-c=/usr/local/bin/xmlrpc-c-config
```Then type the following as usual:
```

make
install
```Clean the mesh you did:
```
cd ..
rm -Rf rtorrent-*
```You have succesfully compiled and installed rtorrent!! =D>
Let's test rtorrent by typing
```
rtorrent
```in the terminal. If rtorrent starts then everything is working fine. Hit CTRL+Q to stop rtorrent.

If you get an error of the style "*Can't find shared library object libtorrent.so.**" then you have probably installed the libtorrent into a folder which is not checked. To troubleshoot this search first for the location of the file by typing
sudo find / -iname "*libtorrent.so*"
replacing the second asterisk so it matches the object in the error message. You would fortunately get a path to that object. In Debian I get as result ```
/usr/local/lib/libtorrent.so.14
```So we assume that libtorrent library is installed in */usr/local/lib/*. Now we have to tell the operating system to look in there as well when checking for libraries. We type
 ```
sudo vim /etc/ld.so.conf
```and add
```
include /usr/local/lib
```Then run ldconfig to update and rerim rtorrent. It should work now!


There is still **one last thing to do**. We have to tell rtorrent how to communicate with rutorrent if we are going to use it. Rtorrent searches for a configuration file everytime it runs. By default there isn't a configuration file so we have to create it. The configuration file is called .rtorrent.rc and should be located in your home directory. If you already have this file from before then you can skip this step(but don't forget to add the lines mentioned later). Let's get in there!:
```
cd ~
```Make a configuration file:
```
touch .rtorrent.rc
```Copy/paste [this]("http://pastebin.com/K4xM69sD") into it and save. What that essentially is, is the latest .rtorrent.rc template from [here]("http://libtorrent.rakshasa.no/browser/trunk/rtorrent/doc/rtorrent.rc?rev=latest") as today(26/Oct/2011) with one extra line at the end:

```
scgi_port = 127.0.0.1:5000
```This tells rtorrent which port and what IP to use to connect with rutorrent. This is **NOT** the port used to download/upload torrents.

Once done with all this it's time to test everything.
Start rtorrent with 
```
rtorrent
```and navigate to
```
http://192.168.1.x/rutorrent
```in your browser. If everything is set correctly you should now see the rutorrent interface with no errors! =D>
[/INDENT]EXTRAS FOLLOWS...
[SIZE=1]





[/SIZE][SIZE=2]**[FONT=Arial Black]4. Running rtorrent as a daemon:twisted:[/FONT]**

[/SIZE]In order to benefit from rutorrent you need to run rtorrent as a daemon(service). By default rtorrent can't run as daemon and if you run rtorrent from a ssh season, rtorrent will terminate once you close that terminal window. To get around we will use a programm called dtach.

The reason we use dtach and not screen(an other similar program) is that dtach is much smaller and is more than enough for our use. To install type
```
sudo apt-get install dtach
```How dtach is being used is simple. To start rtorrent as a daemon type
```
dtach -n /tmp/rtorrent.dtach rtorrent
```where /tmp/rtorrent.dtach is the file to save the season. Once typed that check that the season file was created with
```
ls /tmp
```If you see the rtorrent.dtach file listed then you can asume that rtorrent is running. You can also check by checking on your browser [http://192.168.1.x/rutorrent](http://192.168.1.x/rutorrent)

**[COLOR=Red]ATTENTION[/COLOR]**: /tmp folder is being emptied on Debian on every reboot

If you want to regain control of your program type
```
dtach -a /tmp/rtorrent.dtach
```[SIZE=2]
[/SIZE]



**[FONT=Arial Black][SIZE=2]5. Autostart rtorrent on boot[/SIZE][/FONT]**

Use [this]("http://www.karlrixon.co.uk/articles/linux/start-rtorrent-automatically-at-boot-on-debian-ubuntu/") method to setup rtorrent to autostart on boot easily.

---

