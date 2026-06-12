---
title: "Adding Pandora stations to mythtv's main menu"
date: 2009-11-28
forum: Multimedia Software
---

### Post by greg963 on 2009-11-28
The attached perl script will add yours (or any pandora users) stations to your mythtv menus.  This is acomplished by adding a Pandora menu option to the main menu and building individual prism apps for each of your stations which are then launched from a new mythtv menu. The script is designed to work with mythbuntu but I added options so that a user can adapt it to other distributions. I hope some folks find it useful.

Screenshot examples attached.

**First install some prereqs**
```

sudo apt-get install prism libxml-libxml-perl imagemagick p7zip-full 
sudo apt-get install flashplugin-nonfree 
##Or use whatever flash plugin you prefer, prism will use the same flash plugin as firefox.

```  

Launch prism, this will create the default profile and you can close it without filling in any of the requested info.
```

prism

```

**Download and execute**
Download the attached file and rename it to pandora_parse.pl (or whatever you see fit) and make it executable.
```

mv pandora_parse.txt pandora_parse.pl
chmod +x pandora_parse.pl

```

Execute the script (use sudo, otherwise the changes will not be made to the mythtv menus) using the desired pandora account(s).

```

sudo ./pandora_parse.pl -n account1 -n account2

```

To enable the channel icons in your mythtv use the --theme <your mythtv theme name> option.

```

sudo ./pandora_parse.pl -n account1 -n account2 --theme Mythcenter-wide

```

Note: You can run pandora_parse.pl -? for additional options.

Restart MythFrontend and you should see a menu selection for "Listen to Pandora"
You can run the script at any time to update your stations or run as a cron job to keep your stations current. 

**Pandora HotKeys**
```

Play/Pause: spacebar
Skip Song: right-arrow key
"Thumbs Up" - I like this song: plus key
"Thumbs Down" - I don't like this song: minus key
Increase Volume: up-arrow key
Decrease Volume: down-arrow key
Maximum Volume: shift key and up-arrow key combination
Mute Volume: shift key and down-arrow key combination
Close Alt+F4

```

**Lirc Integration**
To get lirc to work properly I primarily used irxevent, but I also had to put together a couple hacks to deal with some strangeness regarding the flash plugin and focusing.  

First when pandora launches it does not have focus so I created this script to give it focus using xdotool
```

apt-get install xdotool

```

create /usr/local/bin/pfocus and add the following
```

#!/bin/bash

cur=$(/usr/bin/xdotool getwindowfocus)
wid=$(/usr/bin/xdotool search Pandora | head -1)
if [ $wid == $cur ]; then
        # the following coordinates may need to be adjusted depending on your screen size
	/usr/bin/xdotool mousemove 245 170 
	/usr/bin/xdotool click 1
fi
exit 0

```

create /usr/local/bin/pclose and add the following
```

#!/bin/bash

cur=$(/usr/bin/xdotool getwindowfocus)
wid=$(/usr/bin/xdotool search Pandora | head -1)
if [ $wid == $cur ]; then
        /usr/bin/xdotool key Alt+F4
fi
exit 0

```

     To use the above scripts set them up to launch via irexec, I have set my up and down buttons to launch the pfocus script which then moves the mouse within the flash player area of the screen and sends a click. After this I can use the remaining buttons that are configured via irxevent (add irxevent to your session startup).  The pclose script solves several issues caused by a combination of irxevent, xfce, and the flash plugin that would otherwise prevent prism from exiting.

     Here is an example of the relevant portion of my ~/.lircrc file your remote name will differ, you may or may not need to modify the button names and you may need to tweak some other settings as well. 

```

begin
    remote = dvd191
    prog = irxevent
    button = play
    config = Key space Pandora
    repeat = 0
    delay = 0
end

begin
    remote = dvd191
    prog = irexec
    button = stop
    config = /usr/local/bin/pclose
    repeat = 0
    delay = 0
end

begin
    remote = dvd191
    prog = irexec
    button = exit
    config = /usr/local/bin/pclose
    repeat = 0
    delay = 0
end

begin
    remote = dvd191
    prog = irxevent
    button = right
    config = Key Right Pandora
    repeat = 0
    delay = 0
end

begin
    remote = dvd191
    prog = irxevent
    button = left
    config = Key Left Pandora
    repeat = 0
    delay = 0
end

begin
    remote = dvd191
    prog = irexec
    button = up
    config = /usr/local/bin/pfocus
    repeat = 0
    delay = 0
end

begin
    remote = dvd191
    prog = irexec
    button = down
    config = /usr/local/bin/pfocus
    repeat = 0
    delay = 0
end

begin
    remote = dvd191
    prog = irxevent
    button = pause
    config = Key space Pandora
    repeat = 0
    delay = 0
end

begin
    remote = dvd191
    prog = irxevent
    button = ok
    config = Key space Pandora
    repeat = 0
    delay = 0
end

begin
    remote = dvd191
    prog = irxevent
    button = chan-down
    config = Key minus Pandora
    repeat = 0
    delay = 0
end

begin
    remote = dvd191
    prog = irxevent
    button = chan-up
    config = Key plus Pandora
    repeat = 0
    delay = 0
end

begin
    remote = dvd191
    prog = irxevent
    button = forward
    config = Key Right Pandora
    repeat = 0
    delay = 0
end


```

Restart X once you have finished editing your .lircrc

Additional Notes:
The script can be run a normal user and will create the pandora.xml file in the current directory.  It will still create the prism webapps in ~/.pandora/<pandora-username> but it will not modify mythtv (or more specifically it will not modify the mythtv menus unless it has permissions to do so).  Also this was tested on karmic with the most recent version of prism (1.0~b2+svn20090813r49078-0ubuntu1) from the standard ubuntu repositories.

---

### Post by sceo on 2009-12-01
It is sensible for the script to take a long time to run.  I have a lot of stations and it built them all, then I got an error for my QuickMix with ImageMagick:
convert: unable to open image `/home/cwells/.pandora/MYUSERNAME/.MOSTOFMYUSERNAMEs_QuickMix/MOSTOFMYUSERNAMEs_QuickMix.png': No such file or directory @ blob.c/OpenBlob/2439.

Running top, I saw that 7z was commanding my CPU.  It took about 30 minutes for the .pl script to run for me.

---

### Post by greg963 on 2009-12-01
> **sceo said:**
> It is sensible for the script to take a long time to run.  I have a lot of stations and it built them all, then I got an error for my QuickMix with ImageMagick:
convert: unable to open image `/home/cwells/.pandora/MYUSERNAME/.MOSTOFMYUSERNAMEs_QuickMix/MOSTOFMYUSERNAMEs_QuickMix.png': No such file or directory @ blob.c/OpenBlob/2439.

Running top, I saw that 7z was commanding my CPU.  It took about 30 minutes for the .pl script to run for me.

Depending on the power and speed of your mythtv box it may take longer, I only have about 20 stations and it does not take very long, on my particular machine it takes about 1-2 seconds per station. Nonetheless, I updated the script to only create the station images if specifically requested with the --image option.  This should improve the speed a bit (The station image is really not needed since it only appears in the titlebar or if you create a desktop shortcut). 

(New 1.2 version of the script is attached to the first post)

Did the error kill the script or did it continue to run after the error occurred?

Also I would be interested to hear if the change to the script improves your speed significantly, I tested it briefly and it seems to make a big difference it cut down the time per station to a fraction of a second on my slowest machine (single core Athlon 1.8ghz, 2gb ram)

---

### Post by sceo on 2009-12-01
The error did NOT halt the processing, everything ran pretty smooth (I guess that means it wasn't an error, but a warning?), just slow.

The new script no longer gives me the error, but 7z is still pwning my CPU and the script still takes a long time to run.  It's specifically 7z that's taking so long (not `convert` or anything with the images it seems).  I have only 512 of RAM (`top` shows), but a 2.53( or 2.66?) GHz single-core Intel Celeron:

Mem:    476940k total,   471552k used,     5388k free

7z is only grabbing < 2% of memory (compared to mythfrontend which has 11%).

Anyway, I think the script is working just fine and it's probably my not-so-beefy machine (I have 22 stations including the QuickMix).  Running this overnight with cron is not going to be an issue, even if it does take a half hour.

The Back/Exit button and starting the stations all works with the remote, which is awesome.  My other buttons aren't working (that is, it seems irxevent isn't working, but irexec is), and I double-checked I have all the right button names for my remote and stuff.  Incidentally, I followed suit and my .lircrc file just includes another file that I made called "pandora" where I pasted my commands.

Is the intent that you first need to grab focus by pressing "up" and then you can use all the other buttons?  I grab focus with up, but then only closing works.

The images that get made, should those be useable with the default MythTV theme (that shows thumbnails for every menu item entry)?  If that SHOULD work, it's not, if not - how can I use the generated thumbnails in this way?

---

### Post by greg963 on 2009-12-01
> 
7z is still pwning my CPU


I am not sure why 7zip would be hitting you cpu that hard, all I can think is it must be related to the processor architecture, I only have amd64 bit immediately available for testing, but you can also try modifying the compression level like this.

```

pandora_parse.pl -n accountname --zipper  '/usr/bin/7z a -mx0 -tzip'  

```

The -mx# sets the compression, see the link below for more examples, the default is 5.
[http://dotnetperls.com/7-zip-examples](http://dotnetperls.com/7-zip-examples)

> 
it seems irxevent isn't working


Make sure irxevent is running with 'ps -ef | grep irxevent' if not add it to you session startup. 

On Mythbuntu
Applications->Settings->sessions and Startup->Autostart Applications->Add
command should be /usr/bin/irxevent
then restart X

> 
Is the intent that you first need to grab focus by pressing "up" and then you can use all the other buttons? I grab focus with up, but then only closing works.


Yes, that is the intent
Also double check that the flashplayer does have focus by pressing the appropriate button on the remote then testing with the keyboard.

> 
The images that get made, should those be useable with the default MythTV theme (that shows thumbnails for every menu item entry)? If that SHOULD work, it's not, if not - how can I use the generated thumbnails in this way?


No they are not added to myth... but that is a good idea, I'll look into it.  The images will still be available in ~/.pandora/<uname>/.<Stationname>/.<Stationname>.png
for example:
/home/gregnuj/.pandora/White_Christmas_Radio/.White_Christmas_Radio.png

I have not quite figured out the theme structure in mythtv yet, If anyone reading this knows how to set the menu images used in mythtv, some insight would be appreciated.

---

### Post by sceo on 2009-12-01
OK, so that TOTALLY explains why I've NEVER been able to make irxevent work... cuz it's a daemon!  *sigh* -- luff it when it's like the first sentence of the man page.

So - everything seems to be working QUITE well now as far as the remote is concerned.

And, for the 7z thing, I found a recursion in the directory structure, which I think might be part of the problem... ?

Inside my home folder, there's this:
...
drwxr-xr-x  2 cwells cwells   4096 2009-12-01 10:47 .CHRISTMAS
-rwxr-xr-x  1 cwells cwells 281464 2009-12-01 15:33 CHRISTMAS.webapp
drwxr-xr-x  2 cwells cwells   4096 2009-12-01 10:48 .christopherj.wells's_QuickMix
drwx------  3 root   root     4096 2009-12-01 10:48 christopherj.wellss_QuickMix.webapp 
drwxr-xr-x  2 cwells cwells   4096 2009-12-01 10:48 .Cool_Jazz
-rwxr-xr-x  1 cwells cwells 127116 2009-12-01 15:33 Cool_Jazz.webapp
...

Note that there's a DIRECTORY called "christopherj.wellss_QuickMix.webapp", which is owned by root. Inside it there's a whole /home/cwells/.pandora folder inside, with a file in it called "*.zip" -- is that what it's supposed to be doing?

Think it would be easy to try and use "zip" instead of "7z" in the script?  I'm a programmer, but not a Perl programmer.  :)

---

### Post by greg963 on 2009-12-01
Ok, I added a -zip option to the script that will cause it to use zip instead of 7z.  Also based on what you mentioned about recursion I added some additional code to deal with odd characters in the username.  I am not exactly sure what caused the problem, but if this does not fix it, if you PM me your pandora username I can test the script using it.

```

pandora_parse.pl -zip -n accountname

```

---

### Post by sceo on 2009-12-01
I'll try it with -zip and see how it goes.  I used my email address as my Pandora username (cuz that's what I log in with).  Is it something else?  It's got two periods in it (and obviously an @ - which could be the problem).

UPDATE: Using -zip or using regular 7z, it works in < 1 min now.  It was definitely the recursion problem.

P.S. With this thing working, THIS IS *AWESOME* and I have not yet commended you for how FANTASTIC this is... makes me SO happy.  I'm going to look into getting the images into the menu, I'll let you know what I find.

---

### Post by sceo on 2009-12-01
/usr/share/mythtv/themes/Terra/watermarks has all the images for the Terra theme

and /usr/share/mythtv/themes/Terra/menu-ui.xml has all the references to it.

So far I've not found it possible to override a theme's menu-ui.xml - seems you could only edit it directly ([http://www.gossamer-threads.com/lists/mythtv/users/405556](http://www.gossamer-threads.com/lists/mythtv/users/405556)).

I'm not keen to wade through the mythtv source code, so I'm considering just changing to a text-only theme ;)

---

### Post by greg963 on 2009-12-01
> 
UPDATE: Using -zip or using regular 7z, it works in < 1 min now. It was definitely the recursion problem.

Yes, initially I had forgotten to do a global replace for special characters in the filename regex, I can't quite figure out what it was doing, but it probably did have something to do with the @ like you mentioned.

Glad you like it! I am looking at the themes too.

---

### Post by greg963 on 2009-12-02
Ok, I found whay I needed to know about themes here.
[http://www.mythtv.org/wiki/MythUI_Theme_Development#The_imagetype_widget](http://www.mythtv.org/wiki/MythUI_Theme_Development#The_imagetype_widget)

I have updated the script (v1.4) to allow a theme to be identified on the commandline with the --theme option.  .  Also it will only do the updates if the user updating the script has write permissions to the themes so use sudo.

```

sudo pandora_parse.pl --name youraccount --theme MythCenter-wide
# Use the theme name you want to modify, the theme name is case sensitive.

```

This should work with any theme, but I have only tested it so far with MythCenter, but it makes a copy of the original menu-ui.xml file so to undo the changes you can always:

```

cd /usr/share/mythtv/themes/<ThemeName>
sudo cp menu-ui.orig menu-ui.xml 

```

Then restart mythfrontend

---

### Post by sceo on 2009-12-02
Worked like a champ for Terra (default)!  Genius!  This is huge, imo.  :)

---

### Post by jquintana on 2010-01-11
First of all, thanks for the script. I have it working, somewhat. The only problem is that when it creates the pandora.xml file it is not reading the correct pandora account. I have tried 2 different accounts and neither one is being populated with the right stations.

Any help is greatly appreciated!

---

### Post by greg963 on 2010-01-11
The stations are pulled from pandora's RSS feed you may want to look here
[http://www.pandora.com/feeds/](http://www.pandora.com/feeds/)
and see what your stations link is.  

I can only guess at the reason without more information, but I am guessing your username might not be unique, I am not sure how pandora handles this when it generates the feed urls, but I think if I allow the script to use your full email address that might fix it.  I have modified the script accordingly so re download and give it a shot.

If this still doesn't work PM me your pandora username and I can do some more troubleshooting.

---

### Post by jquintana on 2010-01-11
> **greg963 said:**
> The stations are pulled from pandora's RSS feed you may want to look here
[http://www.pandora.com/feeds/](http://www.pandora.com/feeds/)
and see what your stations link is.  

I can only guess at the reason without more information, but I am guessing your username might not be unique, I am not sure how pandora handles this when it generates the feed urls, but I think if I allow the script to use your full email address that might fix it.  I have modified the script accordingly so re download and give it a shot.

If this still doesn't work PM me your pandora username and I can do some more troubleshooting.Thanks I will download it this evening.

---

### Post by jquintana on 2010-01-12
The new script accepted my email and I now have access to all my stations.

This may be outside the scope of this script but is there a way to add a background image to the "Listen to Pandora" menu option?

---

### Post by icebeer2875 on 2010-02-05
I tried what you described, unfortunately something went wrong for me. It found the stations I have in pandora, and it added the menu to my theme, but when I try to play it it says "Myth could not locate the menu file pandora.xml"

I would really appreciate some help, this would be an awesome thing to get working :)

EDIT:

Nevermind, I was putting the generated pandora.xml file in the wrong directory!

This is awesome, thanks again for posting this!

---

### Post by 89vision on 2010-05-01
The script runs just fine but then when I go to listen it says that mythtv can't find pandora.xml.  pandora.xml is in my home directory, is that where it's suppose to be?

---

### Post by Nausser on 2010-06-22
Ok... I seem to need a bit more help than the average person. I've gotten Pandora added to my Mythfrontend and have all my stations there to listen to. My headache is from trying to get my remote to control it all.

I can exit fine by pressing Alt+F4 with no problems. I've altered the remote commands to use mceusb and changed the buttons to reflect it's settings/config and added the button presses to my .lircrc file. I couldn't start irxevent so I installed lirc-x and now have started irxevent by running "irxevent -d" command. 

I still have zero commands working via my remote. I must be missing something silly, I hope.

The only bit of information that I have no idea what to do with or if I even need to do anything with is the "***Pandora Hotkeys***" section. I assume these are just notes on what keys do what but if not, I don't see where this code would go.

Also, I don't seem to have any keyboard control besides the Alt+F4 to close and return to Mythtv Pandora channels.

Thank you for any help you may be able to offer!

--------------------------------------------------------------------------------------------------------

Update:

Good news. All is now working. What I failed to do is make the two files executable.

sudo chmod +x /usr/local/bin/pfocus
sudo chmod +x /usr/local/bin/pclose

Added "irxevent -d" to my startup programs and now all is well. Also added my Volume Up and Down for complete control.

Here are the updates I added to my "~/.lircrc" file just in case it helps someone else:

"begin
    remote = mceusb
    prog = irxevent
    button = VolUp
    config = Key Up Pandora
    repeat = 1
    delay = 2
end

begin
    remote = mceusb
    prog = irxevent
    button = VolDown
    config = Key Down Pandora
    repeat = 1
    delay = 2
end

begin
    remote = mceusb
    prog = irxevent
    button = Play
    config = Key space Pandora
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = irexec
    button = Stop
    config = /usr/local/bin/pclose
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = irexec
    button = exit
    config = /usr/local/bin/pclose
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = irxevent
    button = Right
    config = Key Right Pandora
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = irxevent
    button = Left
    config = Key Left Pandora
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = irexec
    button = Up
    config = /usr/local/bin/pfocus
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = irexec
    button = Down
    config = /usr/local/bin/pfocus
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = irxevent
    button = Pause
    config = Key space Pandora
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = irxevent
    button = OK
    config = Key space Pandora
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = irxevent
    button = ChanDown
    config = Key minus Pandora
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = irxevent
    button = ChanUp
    config = Key plus Pandora
    repeat = 0
    delay = 0
end

begin
    remote = mceusb
    prog = irxevent
    button = Forward
    config = Key Right Pandora
    repeat = 0
    delay = 0
end"

I made the Volume Up and Down buttons repeat for obvious reasons.

---

### Post by Nausser on 2010-06-23
Now that I am enjoying Pandora on my Myth system.... I hate the ads and interruption of the "Are you still listening?". Of which there is no way to click that you are still listening unless you break out the keyboard or mouse. Not really ideal there. I can of course exit and re-select the Pandora channel and be off for a while again. (with commercials)

I guess this stands out for me because I was an early adopter of the Chumby. I absolutely love my Chumby! I really love that Pandora can play on a Chumby for days and never get interrupted or hear a commercial! I know Chumby is an open source system. Can to two be merged somehow. I mean the Chumby Pandora widget and MythTV.

I'm not a huge coder, more of a systems admin. Does anyone out there think it may be possible to make Pandora on MythTV function like the Pandora widget on Chumby does? Can we make it connect the same way to Pandora's music servers?

Let me know your thoughts!...

---

### Post by Nausser on 2010-09-03
In learning of and installing Boxee, I no longer use MythTV for Hulu or Pandora. Boxee's Pandora app is all ready to go and works far better. The main advantage is there are no ads, only non-stop music of choice!

It certainly isn't a direct fix for Mythbuntu but thanks to the wonders of lirc, I have an extra button programmed on my remote, one for Mythbuntu and one for Boxee. This way I can switch between them easily and quickly. I used the following forum to configure irexec to my likings.
Look at ding's post at the top of page 3:
[http://forums.boxee.tv/showthread.php?t=4248&page=3]("http://forums.boxee.tv/showthread.php?t=4248&page=3")

I hope this is helpful!

---

### Post by Nausser on 2010-09-03
> **89vision said:**
> The script runs just fine but then when I go to listen it says that mythtv can't find pandora.xml.  pandora.xml is in my home directory, is that where it's suppose to be?

It needs to go in your theme's folder.
/usr/share/mythtv/theme/*your_theme*/

---

### Post by kirov on 2010-11-01
hello greg963,

thanks for all the owrk you put into this.

Hopefully the following will help others...

I was having an issue getting pandora_parse.pl to complete. it kept exiting with the following:

Empty String at ./pandora_parse.pl line 198

I've checked my username and can grab the RSS feed from the browser and noticed my privacy settings were stopping the script from retrieving my stations. Logged into Pandora and changed my security settings.

---

### Post by Digicrat on 2010-12-24
This is a nice little script and works great, thanks.


One lesson learned on getting LIRC working: Do NOT copy & paste the lirc config file from Firefox to nano in an SSH terminal under Windows.  The resulting file somehow picked up invalid characters (and not the usual line-endings) that caused a syntax error.  


Also, for pre-requisites, the following is needed to get irxevent:
```
sudo apt-get install lirc-x
```

irxevent and irexec are started using the following, and should be added to startup (Settings->Sesison and Startup->Autostart):
```

irxevent -d
irexec -d

```

---

