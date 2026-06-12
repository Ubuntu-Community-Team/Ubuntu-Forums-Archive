---
title: "How I Integrated some X10 Home Automation into MythBuntu"
date: 2008-04-17
forum: Mythbuntu
---

### Post by freymann on 2008-04-17
I had bought some X10 equipment and did some searching to see how I could integrate it into MythBuntu. I think I utilized two different web pages and did some customizing of my own, and figured I would document what I did here for anybody else interested in doing the same thing!

First, my list of equipment:

RCA X10 ActiveHome PC Interface (CM11A)
6 dimmable lamp modules (LM465)

For future use, I have a

2-way transceriver module (RR501)
and I just bought some more equipment (KR22A, LM15A, AM466, WS12A) and I have some more items to purchase later like SS13A, SR227, XPS3. I usually purchase 3-packs, and I order everything off this eBay store:

[http://stores.ebay.ca/X10-WAREHOUSE]("http://stores.ebay.ca/X10-WAREHOUSE")

Total cost of my initial equipment was under $40 US before shipping.

Now, on to the X10 setup!

First I had to download, compile and install Heyu. Go here:

[http://www.heyu.org/download/]("http://www.heyu.org/download/")

Copy that to your home directory.

Before I could compile (on MythBuntu 7.10) I had to do this:

```

sudo apt-get install build-essential

```

Now you need to unzip/untar the heyu file.

```
 tar -xvzf heyu***.tgz
```

(replace *** with the version or filename you downloaded)

That should put everything into a directory of its own.

You might want to install the batteries into the CM11A and connect the serial cable between the computer and controller, and then plug the controller into a socket now.

Back to compiling Heyu... I just followed the instructions in the INSTALL file. Very easy to do. I put the config into /etc/heyu/ 

```

 sh ./Configure  [option]   (As a normal user)
 make                       (As a normal user)
 su                         (Become superuser)
 make install               (As superuser)
 exit                       (Revert to normal user)
 heyu info                  (As a normal user, to test installation)

```

So now, heyu should be installed and your CM11A is connected.

Time to take some of your lamp modules, give them a unique house code and number, plug in some lamps. You may find it easy to assign a "room" or an area with one housecode and then number each lamp. Write down on a piece of paper what each lamp module is controlling for reference later!

Now let's test things to see if we can flip on a light.

```

heyu on E1

```

In my case, E1 is a Lamp in the living-room. Presto! It comes on!

```

heyu off E1

```

and the lamp turns off. I test some of the other lamp modules to ensure they were working too.

There's plenty of instructions with heyu to get you going. Look in the directory you compiled the program in for sample config files and commands. I'm not going to go into details on everything heyu can do. Their site has support for that.

Assuming you were lucky and the lamps are working remotely, time now to integrate some commands into MythTV.

I based what I was doing off this page:

[http://mythtv.org/wiki/index.php/X10]("http://mythtv.org/wiki/index.php/X10")

The only difference was I was using heyu so I had to modify the x10lights script somewhat. My version of the x10lights script contains the following:

```

#!/bin/bash
# Control for X10 lights in Myth

if [ "$1" = "tv" ]; then
        # 1st we give a lightson then turn off the lights we dont want 
        /usr/local/bin/heyu lightson E
        /usr/local/bin/heyu off E1
        /usr/local/bin/heyu dim E2 8
        /usr/local/bin/heyu off E3


elif [ "$1" = "movie" ]; then
        # 1st we give a lightson then turn off all the lights except one
        # and dim that one to about 50% 
        /usr/local/bin/heyu lightson E
        /usr/local/bin/heyu off E1
        /usr/local/bin/heyu off E2
        /usr/local/bin/heyu dim E3 12

elif [ "$1" = "aon" ]; then
        # turn all lights on in house code E
        /usr/local/bin/heyu lightson E

elif [ "$1" = "aoff" ]; then
        # turn all lights on in house code E
        /usr/local/bin/heyu lightsoff E

else
        exit 1
fi
exit 0

```

 and I opted to place this file into ~/.mythtv/ Note that with Mythbuntu 7.10, mythtv runs under the first user you created, so that directory is under my personal home directory.

 chmod 755 ~/.mythtv/x10lights

 to make it executable. I used commands that satisfy heyu and me. You will have to adjust the script to suit your setup. The dim mode seems to be a number between 1 and 22 so you'll need to experiment to find a suitable dimness to your liking.

 Then I backed up the default theme

```

# cd /usr/share/mythtv
# tar cfvz default_backup.tar.gz *.xml

```

I added the following to my mainmenu.xml file.

```

<button>
      <type>MENU_HOME_CONTROL</type>
      <text>Home Control</text>
      <action>MENU home_control.xml</action>
   </button>

```

Then, I created the home_control.xml file (be sure to add all of the stations you want access to):

```
sudo pico home_control.xml
```

and inserted this into the file and saved:

```

<mythmenu name="X10MENU">

   <button>
      <type>LIGHTS</type>
      <text>Lights to TV Mode</text>
      <action>EXEC ~/.mythtv/x10lights tv</action>
   </button>

   <button>
      <type>LIGHTS</type>
      <text>Lights to Movie Mode</text>
      <action>EXEC ~/.mythtv/x10lights movie</action>
   </button>

   <button>
      <type>LIGHTS</type>
      <text>All Upstairs Lights On</text>
      <action>EXEC ~/.mythtv/x10lights aon</action>
   </button>

   <button>
      <type>LIGHTS</type>
      <text>All Upstairs Light Off</text> <action>EXEC ~/.mythtv/x10lights aoff</action>
   </button>

</mythmenu>

```

  I exited MythFrontend and reloaded, cursor'd my way to the home automation page, and tested my 4 functions. Voila! Working! kewl.

 Now that's neat, but who wants to be forced to make their way back to the menu system to control your lights! especially if you're in the middle of watching a recording!?

 Time to reprogram those 4 pretty coloured buttons on the bottom of my remote!

 For this, I referenced the following web site:

[http://www.instructables.com/id/SETFTWRF9056RFG/]("http://www.instructables.com/id/SETFTWRF9056RFG/")

 I had adjust things for my configs, but what I had to change was pretty minor.

 My .lircrc file was in my personal home directory, so I edited it and looked for "Red" and found only one instance of it, in the program elisa. None of the other colors were used. So, I added the following lines to the very top of my ~/.lircrc file:

```

begin
    remote = mceusb
    prog = irexec
    button = Red
    config = /home/freymann/.mythtv/x10lights aoff &
end

begin
    remote = mceusb
    prog = irexec
    button = Green
    config = /home/freymann/.mythtv/x10lights aon &
end

begin
    remote = mceusb
    prog = irexec
    button = Yellow
    config = /home/freymann/.mythtv/x10lights tv &
end

begin
    remote = mceusb
    prog = irexec
    button = Blue
    config = /home/freymann/.mythtv/x10lights movie &
end

```

 Saved the file and then I just restarted the box.

 Now when the MythTV screen appeared, I grabbed the remote and I pressed the Green button and all my living-room lights came on! I used the Red button to shut them all off. Yellow leaves one light on in the corner, slightly dimmed, which is good for regular TV watching, and Blue shuts everything off but one light in the china cabinet, and dims that, which is good for movie watching.

 By programming the coloured buttons, I'm able to control the lights while watching TV or other recordings, etc. No more exiting back to the menus.

 I did a little reading on heyu ("heyu help" has loads of info) and was able to create a small /etc/heyu/x10.sched file to control a small light at the bottom of our stairs. I had a timer plugged into the wall that would turn the light on and off, but heyu and a lamp module can do the same thing (and the lamp module is cheaper than the timer!). 

 You may want to play with the dusk and dawn settings here too, but for my needs, because it is dark in the basement early, I opted to simply turn the light on/off at set times each day of the week. 

 My /etc/heyu/x10.sched file contains:

```

timer  smtwtfs    01/01-12/31 20:00 00:59   blighton  blightoff
macro  blighton  0  on  B1
macro  blightoff 0  off B1

```

which simply means, everyday of the year, turn on B1 at 8pm and turn it off at 1am.

I decided to add the garage outside lights to the schedule, taking advantage of the dusk option, so now my /etc/heyu/x10.sched file contains:

```

timer  smtwtfs    01/01-12/31 dusk-10 00:59   blighton  blightoff
macro  blighton  0  on  B1
macro  blightoff 0  off B1
timer  smtwtfs    01/01-12/31  dusk  23:00  garage_on   garage_off
macro garage_on  0  on  G1
macro garage_off 0  off G1

```

 I thought I would issue the "heyu upload" command, but it told me I had to set my latitude and longitude, so I googled my location and found what I needed for a town close to us and put that in the /etc/heyu/x10.conf file and tried again. This time it worked.

 When I came downstairs this morning, my little light was off.

 You can have heyu log things too, which is handy when you're getting started. 

 So there you go. I have a few lamp modules under X10 control upstairs. I can control the lights through the MythTV menu system or by clicking on the colored buttons on my remote.

 Heyu is acting as a timer and controlling a light in the basement and our outside garage lights!

 My next project is figuring out how I can make some of my extra lamp modules  control lights in the basement station. I'm thinking I can perhaps write up a small php script and install it on the living-room machine, expand upon the x10lights script some more, and then program the coloured remote buttons in the basement to use curl and request the php script off the web server in the living room? I don't see why that wouldn't work. Then I could do the same in the master-bedroom station. 

 I hope that helps somebody else have some fun with X10 under MythBuntu. I'm by no means an expert, and you don't need to be either! Enjoy!

---

### Post by elj4176 on 2008-04-17
Thanks for the writeup! I'll be doing something similar soon and this will help.

---

### Post by freymann on 2008-04-18
This part of the tutorial is going to show how I managed to get one of my other mythtv stations to control lights, even though it doesn't have the CM11A controller attached to it. I need to pass commands to the box that *does* have the controller (192.168.0.3 in my case).

I decided I would create a small php script and stick that into the apache web directory on the mythtv station with the CM11A controller, and basically emulate what the ~/mythtv/x10lights file is doing.

So, first I created a file called x10lights.php in /var/www/

```

sudo pico /var/www/x10lights.php

```

and inside is the following:

```

<?

$pgm = 'sudo /usr/local/bin/heyu';

if ($_REQUEST[cmd] == 'upstairs_tv') { 
        # 1st we give a lightson then turn off the lights we dont want 
        exec("$pgm lightson E", $result, $status);
        exec("$pgm off E1", $result, $status);
        exec("$pgm dim E2 8", $result, $status);
        exec("$pgm off E3", $result, $status);
} elseif ($_REQUEST[cmd] == 'upstairs_movie') { 
        # 1st we give a lightson then turn off all the lights except one
        # and dim that one to about 50% 
        exec("$pgm lightson E", $result, $status);
        exec("$pgm off E1", $result, $status);
        exec("$pgm off E2", $result, $status);
        exec("$pgm dim E3 12", $result, $status);
} elseif ($_REQUEST[cmd] == 'upstairs_aon') {
        # turn all lights on in house code E
        exec("$pgm lightson E", $result, $status);
} elseif ($_REQUEST[cmd] == 'upstairs_aoff') {
        # turn all lights on in house code E
         exec("$pgm lightsoff E", $result, $status);
}  elseif ($_REQUEST[cmd] == 'downstairs_aon') {
        # turn all lights on in house code B2
        exec("$pgm on B2", $result, $status);
}  elseif ($_REQUEST[cmd] == 'downstairs_aoff') {
        # turn all lights on in house code B2
        exec("$pgm off B2", $result, $status);
} elseif ($_REQUEST[cmd] == 'downstairs_tv') {
        exec("$pgm on B2", $result, $status);
} elseif ($_REQUEST[cmd] == 'downstairs_movie') {
        exec("$pgm dim B2 15", $result, $status);
}


?>

```

 The command names in this script are different than the script created in my first post so I can keep track of the upstairs and downstairs, and I've added a new light located in the basement, B2.

 I will be expanding upon this to add control to the master-bedroom lights.

 In order to allow the user www-data the ability to talk to the com port through heyu, I used some info I gathered to allow the shutdown option from the menu to work. I issued this command:

```

sudo visudo

```

 and I added:

```

%www-data ALL = NOPASSWD: /usr/local/bin/heyu

```

to the bottom and saved the file.

 I'm going to call up this script, from any of my 3 mythtv boxes, using the command line and 'curl' -- you need to see if you have curl installed on your box. Just issue this command and see what happens:

```

curl http://192.168.0.3/x10lights.php?cmd=basement_aon

```

 If you don't have curl installed, you should see a message telling you how to install it. I followed the suggestion and issued:

```

sudo apt-get install curl

```

 Then I tried my curl command again, and presto! 

 So now we have a 'hook' into the X10 controller that we can reach from any computer in the house through a web browser or on any one of our mythtv boxes via the command line.

 I went to my downstairs mythtv box and I made the similar changes to my ~/.lircrc file:

```

pico ~/.lircrc

```

 and this time I added the following to the very top:

```

begin
    remote = mceusb
    prog = irexec
    button = Red
    config = /usr/bin/curl http://192.168.0.3/x10lights.php?cmd=downstairs_aoff &
end

begin
    remote = mceusb
    prog = irexec
    button = Green
    config = /usr/bin/curl http://192.168.0.3/x10lights.php?cmd=downstairs_aon &
end

begin
    remote = mceusb
    prog = irexec
    button = Yellow
    config = /usr/bin/curl http://192.168.0.3/x10lights.php?cmd=downstairs_tv &
end

begin
    remote = mceusb
   prog = irexec
    button = Blue
    config = /usr/bin/curl http://192.168.0.3/x10lights.php?cmd=downstairs_movie &
end

```

 Compared to my first post, all I've done here is change the config line to utilize curl, which will pass the command I need to the web server that has the CM11A controller, which will in turn control X10 modules anywhere you like!

 I reboot the downstairs (and upstairs) mythtv machines, grab the remote and test. Kewl. 

 I also edited the default theme to add light control there too. The steps are the same as in my first post, but the contents of the home_control.xml file are slightly different, as follows:

```

<mythmenu name="X10MENU">

   <button>
      <type>LIGHTS</type>
      <text>Basement Lights to TV Mode</text>
      <action>EXEC /usr/bin/curl http://192.168.0.3/x10lights.php?cmd=downstairs_tv</action>
   </button>

   <button>
      <type>LIGHTS</type>
      <text>Basement Lights to Movie Mode</text>
      <action>EXEC /usr/bin/curl http://192.168.0.3/x10lights.php?cmd=downstairs_movie</action>
   </button>

   <button>
      <type>LIGHTS</type>
      <text>Basement All Lights On</text>
      <action>EXEC /usr/bin/curl http://192.168.0.3/x10lights.php?cmd=downstairs_aon</action>
   </button>

   <button>
      <type>LIGHTS</type>
      <text>Basement All Light Off</text>
     <action>EXEC /usr/bin/curl http://192.168.0.3/x10lights.php?cmd=downstairs_aoff</action>
   </button>

</mythmenu>

```

(note the action line should be one long line)

 So now I can control my X10 modules on ANY of my mythtv stations.

 You could expand on the php script placed in the web server's directory to do many other things and provide feedback if you wanted to. Use your imagination!

---

### Post by freymann on 2008-05-31
When I upgraded to MythBuntu 8.04, I had to do a couple things differently.

For starters, irexec doesn't seem to load automatically anymore, so I edited /etc/rc.local and added:

```

# By default this script does nothing.

/usr/local/bin/heyu engine
/usr/bin/irexec -d /home/freymann/.mythtv/lircrc

exit 0

```

 This was added to the machine that runs heyu.

 On the other two machines I added the /usr/bin/irexec line only. Thanks to these forums I was given that tip ;-)

 Also after upgrading, I had to edit my ~/.lirc/mythtv file to add the functions to my colored buttons.

 On my other two stations, the remotes don't have the colored buttons, so I reprogrammed the LiveTV button, DVD button and RecTV button and Power button to do what the 4 colored buttons did.

 This is working well.

---

### Post by sketchysunday on 2008-11-18
Sweet guide. Thanks for taking the time, this is exactly what I was looking for.

---

### Post by bmwman on 2008-12-05
Is there a way to post some screenshots and how does it integrate with MythTV exacatly?

---

### Post by freymann on 2008-12-05
> **bmwman said:**
> Is there a way to post some screenshots and how does it integrate with MythTV exacatly?

There's not much to see really.... 

If you edit the default theme you'll have another entry on the menu and a sub page with your options.

Most of the "fun" is all behind the scenes... programming buttons on your remote that send commands to heyu for instance.

For remote stations... programming buttons on your remote that talk to a web server that then sends commands to heyu.

There's really nothing "to see" in a screen grab.

Install heyu, get your X10 lights working with it, then just follow my instructions. If you did everything correctly, then you can "see" your lights turn on and off at the press of a button. 

The button method is the best as opposed to adding a page to MythTV. With the buttons on your remote you can turn on/off lights rather quickly, directly, without the need to have the TV on and cursor up/down to get the onscreen selection.

---

### Post by dougweaver on 2009-02-28
Hi - I'm totally new to Ubuntu so forgive the dumb question.

I've been attempting to install Heyu on my pc using the procedure listed in this thread.
I get all the way to the point where I run the "make install" command.  
I get the following message:

I did not find a Heyu configuration file.
Where would you like the sample Heyu configuration file installed?
1. In directory...
2. In subdirectory...
3. In directory...
4. No thanks, I'll take care of it myself.

... at this point I wish to choose option "1", so I type "1" and press enter.  The command cursor in Terminal just sits there blinking at me.  No text scolls by, nothing happens.

What am I doing wrong?

I'd appreciate any suggestions.  thanks!

---

