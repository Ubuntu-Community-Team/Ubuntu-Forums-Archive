---
title: "Directtv_http.pl Setup Help"
date: 2011-05-05
forum: Mythbuntu
---

### Post by burtm05 on 2011-05-05
I am a bit of a newbie with my Mythbuntu install and need a little help understanding how to implement the directtv_http.pl script. 

I am running Mythbuntu 11.04 with an HD-PVR. I have a DirecTV H24 than I plan to control via the ethernet port. I have all of that configured and running. I have the directtv_http.pl script created in /usr/bin and defined as such in my Video Input - External channel change command. I have also loaded the JSON package.

My sticking point is defining the arguments of the script:

[COLOR=#000000][FONT=Times New Roman][FONT=sans-serif]# get args
$dtv_ip = $ARGV[0];
$sleep_sec = $ARGV[1];
$arg = $ARGV[2];
$chan_num = "";
$numArgs = $#ARGV + 1;
$tune = 1;
$minor = 0;


[/FONT][/FONT][/COLOR]Am I suppose to define these in the External channel change command or somewhere else? Any insight will be helpful, this is just beyond my current knowledge level. If more details are needed I will be happy to provide, feel free to ask. Thanks for the help, I can't wait to get this up and running entirely!

EDIT: Here is the URL to the script [http://www.mythtv.org/wiki/Controlling_DirecTV_Set_Top_Box_(STB)_via_Network](http://www.mythtv.org/wiki/Controlling_DirecTV_Set_Top_Box_(STB)_via_Network)

---

### Post by ian dobson on 2011-05-05
Hi,

From the link:-

Always list the IP address of the receiver first.
Next, type the amount of seconds to sleep after changing the channel.
Next, type "tune" to change the channel, or "getTuned" to display the JSON for the current listing
If you chose "tune", now enter the channel number

So you need to go to mythtv-setup and "tell" mythtv how to tune channels. I think this is option is the card-input screen. YOu need to tell mythtv to start the following script :-

/usr/bin/directtv_http.pl 192.168.0.88 10 tune 

Note you'll have to change the IP address to the IP address of your tuner, 10 is the numer of seconds to wait, tune is the command to be performed, mythtv will then add the channel number to the end of the commend.

Note you'll need to make sure the the script can be executed by the mythtv-user

Note: Make sure mythtv uses the same channel numbers as your tuner.

Hope this helps.

Regards
Ian Dobson

---

### Post by burtm05 on 2011-05-05
Wow, I honestly feel like an idiot. I had read that several times I just didn't make the connection. Thanks for the quick help!

---

### Post by ian dobson on 2011-05-05
Hi,

No problems, in perl $ARGV[]; is an array containing a list of the command line parameters, so the first parameter is in $ARGV[0].

Regards
Ian Dobson

---

### Post by phroman on 2011-05-05
Well, I literally wrote out the exact same post as burtm05, glad I searched first..  

I followed Ian's info, unfortunately it didn't work for me, and it breaks live tv. I definitely know if there's anything wrong with the channel change script in Input Connections in the backend setup, It'll break live tv.  I entered it into the backend-setup like this:

```
/usr/local/bin/directtv_http.pl my-directv-box-IP 10 tune
```

The script is executeable and owned my user Mythtv.  I installed JSON via cpan.  I can change channels on the Directv Receiver from my desktop computer by putting this into a browser window:  
```
my-directv-box-IP:8080/tv/tune?major=7
```

It seems I'm ok on the network setup and that the script functions.  And I will say, it changes channels way faster than it does using the direct tv remote.  There are numerous errors in my backend log.

 Here's my backend log:

```
2011-05-05 15:20:33.889 mythbackend version: fixes/0.24 [v0.24-250-g56c54fa] www.mythtv.org
2011-05-05 15:20:34.021 Using runtime prefix = /usr
2011-05-05 15:20:34.124 Using configuration directory = /home/mythtv/.mythtv
2011-05-05 15:20:34.519 Empty LocalHostName.
2011-05-05 15:20:34.710 Using localhost value of mythserver
2011-05-05 15:20:34.804 Testing network connectivity to '192.168.1.22'
2011-05-05 15:20:35.147 New DB connection, total: 1
2011-05-05 15:20:35.442 Connected to database 'mythconverg' at host: 192.168.1.22
2011-05-05 15:20:35.593 Closing DB connection named 'DBManager0'
2011-05-05 15:20:35.676 Connected to database 'mythconverg' at host: 192.168.1.22
2011-05-05 15:20:36.281 Current locale EN_US
2011-05-05 15:20:36.337 Reading locale defaults from /usr/share/mythtv//locales/en_us.xml
2011-05-05 15:20:36.403 Current MythTV Schema Version (DBSchemaVer): 1264
2011-05-05 15:20:36.449 ThreadPool:HTTP: Initial 1, Max 25, Timeout 60000
2011-05-05 15:20:36.494 Enabling Upnpmedia rebuild thread.
2011-05-05 15:20:37.741 MythBackend: Starting up as the master server.
2011-05-05 15:20:38.048 New DB connection, total: 2
2011-05-05 15:20:38.453 Connected to database 'mythconverg' at host: 192.168.1.22
2011-05-05 15:20:38.882 New DB connection, total: 3
2011-05-05 15:20:39.013 Connected to database 'mythconverg' at host: 192.168.1.22
2011-05-05 15:20:47.312 UPnpMedia: BuildMediaMap VIDEO scan starting in :/disk2/videos:
2011-05-05 15:20:48.901 UPnpMedia: BuildMediaMap Done. Found 1 objects
2011-05-05 15:20:48.955 UPnpMedia: BuildMediaMap VIDEO scan starting in :/disk2/movies:
2011-05-05 15:20:49.640 UPnpMedia: BuildMediaMap Done. Found 411 objects
/usr/local/bin/directtv_http.pl: 2: Cannot fork
/usr/local/bin/directtv_http.pl: 4: use: not found
/usr/local/bin/directtv_http.pl: 5: use: not found
/usr/local/bin/directtv_http.pl: 12: cannot create new: Permission denied
/usr/local/bin/directtv_http.pl: 12: =: not found
/usr/local/bin/directtv_http.pl: 13: Syntax error: "(" unexpected
/usr/local/bin/directtv_http.pl: 4: 2011-05-05 15:21:16.528 New DB scheduler connection
use: not found
/usr/local/bin/directtv_http.pl: 5: use: not found2011-05-05 15:21:17.200 Connected to database 'mythconverg' at host: 192.168.1.22

/usr/local/bin/directtv_http.pl: 12: cannot create new: Permission denied
/usr/local/bin/directtv_http.pl: 12: =: not found
/usr/local/bin/directtv_http.pl: 13: Syntax error: "(" unexpected
/usr/local/bin/directtv_http.pl: 4: use: not found
/usr/local/bin/directtv_http.pl: 5: use: not found
/usr/local/bin/directtv_http.pl: 12: cannot create new: Permission denied
/usr/local/bin/directtv_http.pl: 12: =: not found
/usr/local/bin/directtv_http.pl: 13: Syntax error: "(" unexpected
/usr/local/bin/directtv_http.pl: 4: use: not found
/usr/local/bin/directtv_http.pl: 5: use: not found
/usr/local/bin/directtv_http.pl: 12: cannot create new: Permission denied
/usr/local/bin/directtv_http.pl: 12: =: not found
2011-05-05 15:21:20.665 Reschedule requested for id -1.
/usr/local/bin/directtv_http.pl: 13: Syntax error: "(" unexpected
/usr/local/bin/directtv_http.pl: 4: use: not found
/usr/local/bin/directtv_http.pl: 5: use: not found
/usr/local/bin/directtv_http.pl: 12: cannot create new: Permission denied
/usr/local/bin/directtv_http.pl: 12: =: not found
/usr/local/bin/directtv_http.pl: 13: Syntax error: "(" unexpected
/usr/local/bin/directtv_http.pl: 4: use: not found
/usr/local/bin/directtv_http.pl: 5: use: not found
/usr/local/bin/directtv_http.pl: 12: cannot create new: Permission denied
/usr/local/bin/directtv_http.pl: 12: =: not found
/usr/local/bin/directtv_http.pl: 13: Syntax error: "(" unexpected
/usr/local/bin/directtv_http.pl: 4: 2011-05-05 15:21:39.115 Scheduled 420 items in 18.3 = 5.39 match + 12.87 place
use: not found
2011-05-05 15:21:39.924 Seem to be woken up by USER
/usr/local/bin/directtv_http.pl: 5: use: not found
/usr/local/bin/directtv_http.pl: 12: cannot create new: Permission denied
/usr/local/bin/directtv_http.pl: 12: =: not found
/usr/local/bin/directtv_http.pl: 13: Syntax error: "(" unexpected
/usr/local/bin/directtv_http.pl: 4: use: not found
/usr/local/bin/directtv_http.pl: 5: use: not found
/usr/local/bin/directtv_http.pl: 12: cannot create new: Permission denied
/usr/local/bin/directtv_http.pl: 12: =: not found
/usr/local/bin/directtv_http.pl: 13: Syntax error: "(" unexpected
/usr/local/bin/directtv_http.pl: 4: use: not found
/usr/local/bin/directtv_http.pl: 5: use: not found
/usr/local/bin/directtv_http.pl: 12: cannot create new: Permission denied
/usr/local/bin/directtv_http.pl: 12: =: not found
/usr/local/bin/directtv_http.pl: 13: Syntax error: "(" unexpected
/usr/local/bin/directtv_http.pl: 4: use: not found
/usr/local/bin/directtv_http.pl: 5: use: not found
/usr/local/bin/directtv_http.pl: 12: cannot create new: Permission denied
/usr/local/bin/directtv_http.pl: 12: =: not found
/usr/local/bin/directtv_http.pl: 13: Syntax error: "(" unexpected
/usr/local/bin/directtv_http.pl: 4: use: not found
/usr/local/bin/directtv_http.pl: 5: use: not found
/usr/local/bin/directtv_http.pl: 12: cannot create new: Permission denied
/usr/local/bin/directtv_http.pl: 12: =: not found
/usr/local/bin/directtv_http.pl: 13: Syntax error: "(" unexpected
/usr/local/bin/directtv_http.pl: 4: use: not found
/usr/local/bin/directtv_http.pl: 5: use: not found
/usr/local/bin/directtv_http.pl: 12: cannot create new: Permission denied
/usr/local/bin/directtv_http.pl: 12: =: not found
/usr/local/bin/directtv_http.pl: 13: Syntax error: "(" unexpected
/usr/local/bin/directtv_http.pl: 4: use: not found
/usr/local/bin/directtv_http.pl: 5: use: not found
/usr/local/bin/directtv_http.pl: 12: cannot create new: Permission denied
/usr/local/bin/directtv_http.pl: 12: =: not found
/usr/local/bin/directtv_http.pl: 13: Syntax error: "(" unexpected
/usr/local/bin/directtv_http.pl: 4: use: not found
/usr/local/bin/directtv_http.pl: 5: use: not found
/usr/local/bin/directtv_http.pl: 12: cannot create new: Permission denied
/usr/local/bin/directtv_http.pl: 12: =: not found
/usr/local/bin/directtv_http.pl: 13: Syntax error: "(" unexpected
/usr/local/bin/directtv_http.pl: 4: use: not found
/usr/local/bin/directtv_http.pl: 5: use: not found
/usr/local/bin/directtv_http.pl: 12: cannot create new: Permission denied
/usr/local/bin/directtv_http.pl: 12: =: not found
/usr/local/bin/directtv_http.pl: 13: Syntax error: "(" unexpected
/usr/local/bin/directtv_http.pl: 4: use: not found
/usr/local/bin/directtv_http.pl: 5: use: not found
/usr/local/bin/directtv_http.pl: 12: cannot create new: Permission denied
/usr/local/bin/directtv_http.pl: 12: =: not found
/usr/local/bin/directtv_http.pl: 13: Syntax error: "(" unexpected
/usr/local/bin/directtv_http.pl: 4: use: not found
/usr/local/bin/directtv_http.pl: 5: use: not found
/usr/local/bin/directtv_http.pl: 12: cannot create new: Permission denied
/usr/local/bin/directtv_http.pl: 12: =: not found
/usr/local/bin/directtv_http.pl: 13: Syntax error: "(" unexpected
/usr/local/bin/directtv_http.pl: 4: use: not found
/usr/local/bin/directtv_http.pl: 5: use: not found
/usr/local/bin/directtv_http.pl: 12: cannot create new: Permission denied
/usr/local/bin/directtv_http.pl: 12: =: not found
/usr/local/bin/directtv_http.pl: 13: Syntax error: "(" unexpected
/usr/local/bin/directtv_http.pl: 4: use: not found
/usr/local/bin/directtv_http.pl: 5: use: not found
/usr/local/bin/directtv_http.pl: 12: cannot create new: Permission denied
/usr/local/bin/directtv_http.pl: 12: =: not found
/usr/local/bin/directtv_http.pl: 13: Syntax error: "(" unexpected
/usr/local/bin/directtv_http.pl: 4: use: not found
/usr/local/bin/directtv_http.pl: 5: use: not found
/usr/local/bin/directtv_http.pl: 12: cannot create new: Permission denied
/usr/local/bin/directtv_http.pl: 12: =: not found
/usr/local/bin/directtv_http.pl: 13: Syntax error: "(" unexpected
/usr/local/bin/directtv_http.pl: 4: use: not found
/usr/local/bin/directtv_http.pl: 5: use: not found
/usr/local/bin/directtv_http.pl: 12: cannot create new: Permission denied
/usr/local/bin/directtv_http.pl: 12: =: not found
/usr/local/bin/directtv_http.pl: 13: Syntax error: "(" unexpected
/usr/local/bin/directtv_http.pl: 4: use: not found
/usr/local/bin/directtv_http.pl: 5: use: not found
/usr/local/bin/directtv_http.pl: 12: cannot create new: Permission denied
/usr/local/bin/directtv_http.pl: 12: =: not found
/usr/local/bin/directtv_http.pl: 13: Syntax error: "(" unexpected
/usr/local/bin/directtv_http.pl: 4: use: not found
/usr/local/bin/directtv_http.pl: 5: use: not found
/usr/local/bin/directtv_http.pl: 12: cannot create new: Permission denied
/usr/local/bin/directtv_http.pl: 12: =: not found
/usr/local/bin/directtv_http.pl: 13: Syntax error: "(" unexpected
/usr/local/bin/directtv_http.pl: 4: use: not found
/usr/local/bin/directtv_http.pl: 5: use: not found
/usr/local/bin/directtv_http.pl: 12: cannot create new: Permission denied
/usr/local/bin/directtv_http.pl: 12: =: not found
/usr/local/bin/directtv_http.pl: 13: Syntax error: "(" unexpected
/usr/local/bin/directtv_http.pl: 4: use: not found
/usr/local/bin/directtv_http.pl: 5: use: not found
/usr/local/bin/directtv_http.pl: 12: cannot create new: Permission denied
/usr/local/bin/directtv_http.pl: 12: =: not found
/usr/local/bin/directtv_http.pl: 13: Syntax error: "(" unexpected
/usr/local/bin/directtv_http.pl: 4: use: not found
/usr/local/bin/directtv_http.pl: 5: use: not found
/usr/local/bin/directtv_http.pl: 12: cannot create new: Permission denied
/usr/local/bin/directtv_http.pl: 12: =: not found
/usr/local/bin/directtv_http.pl: 13: Syntax error: "(" unexpected
/usr/local/bin/directtv_http.pl: 4: use: not found
/usr/local/bin/directtv_http.pl: 5: use: not found
/usr/local/bin/directtv_http.pl: 12: cannot create new: Permission denied
/usr/local/bin/directtv_http.pl: 12: =: not found
/usr/local/bin/directtv_http.pl: 13: Syntax error: "(" unexpected
/usr/local/bin/directtv_http.pl: 4: use: not found
/usr/local/bin/directtv_http.pl: 5: use: not found
/usr/local/bin/directtv_http.pl: 12: cannot create new: Permission denied
/usr/local/bin/directtv_http.pl: 12: =: not found
/usr/local/bin/directtv_http.pl: 13: Syntax error: "(" unexpected
/usr/local/bin/directtv_http.pl: 4: use: not found
/usr/local/bin/directtv_http.pl: 5: use: not found
/usr/local/bin/directtv_http.pl: 12: cannot create new: Permission denied
/usr/local/bin/directtv_http.pl: 12: =: not found
/usr/local/bin/directtv_http.pl: 13: Syntax error: "(" unexpected
/usr/local/bin/directtv_http.pl: 4: use: not found
/usr/local/bin/directtv_http.pl: 5: use: not found
/usr/local/bin/directtv_http.pl: 12: cannot create new: Permission denied
/usr/local/bin/directtv_http.pl: 12: =: not found
/usr/local/bin/directtv_http.pl: 13: Syntax error: "(" unexpected
/usr/local/bin/directtv_http.pl: 4: use: not found
/usr/local/bin/directtv_http.pl: 5: use: not found
/usr/local/bin/directtv_http.pl: 12: cannot create new: Permission denied
/usr/local/bin/directtv_http.pl: 12: =: not found
/usr/local/bin/directtv_http.pl: 13: Syntax error: "(" unexpected
/usr/local/bin/directtv_http.pl: 4: use: not found
/usr/local/bin/directtv_http.pl: 5: use: not found
/usr/local/bin/directtv_http.pl: 12: cannot create new: Permission denied
/usr/local/bin/directtv_http.pl: 12: =: not found
/usr/local/bin/directtv_http.pl: 13: Syntax error: "(" unexpected
/usr/local/bin/directtv_http.pl: 4: use: not found
/usr/local/bin/directtv_http.pl: 5: use: not found
/usr/local/bin/directtv_http.pl: 12: cannot create new: Permission denied
/usr/local/bin/directtv_http.pl: 12: =: not found
/usr/local/bin/directtv_http.pl: 13: Syntax error: "(" unexpected
```

On my FE/BE machine, I get the "Can't connect to master backed" when starting Mythfrontend, and my entire system is slow, it takes 2 minutes just to exit the frontend.  How does a channel change script mess with the backend?  It would be great to get this working and have one less cable coming out of the back of my system, and if the speed of channel changing is as fast as it is through a browser, awesome.

  Thanks everyone.

---

### Post by ian dobson on 2011-05-05
Hi,

Does the script work when you run it from the commandline?

Also findout how long it takes to tune to a channel and then use this time for the timeout.

Regards
Ian Dobson

---

### Post by phroman on 2011-05-06
Hi Ian, this seems to be bogging my system down so badly that its unusable, I have to kill the front and backend before I can even do anything at the desktop.

I'm not totally sure how to call it from the command line, I tried a few ways.

```
joe@mythserver:/usr/local/bin$ directtv_http.pl 192.168.1.25:8080 5 tune 11
```

```
joe@mythserver:/usr/local/bin$ directtv_http.pl 192.168.1.25.8080 5 tune 11
```

```
joe@mythserver:/usr/local/bin$ directtv_http.pl 192.168.1.25 5 tune 11
```

All of these result in a hang at the terminal, and no channel change.  

Tried running it from my desktop 10.10 computer like this:

```
  directtv_http.pl 192.168.1.25:8080 5 tune 11 
```

It worked the first time, tried it again and it completely locked up my machine, had to hit the reset button

Thanks for any help.

UPDATE:   

I got it working, I think maybe when I copied the script from the webpage it was on I missed a line or something because I copied it again and it works.  Except, channel changing may actually be a bit slower now.  What really controls how fast my system changes the channel?  I think it was faster on my 9.04 setup than it is on my 10.10.  Is there anything I can do to make it faster?  

Cheers.

---

### Post by ian dobson on 2011-05-06
Hi,

Just try running the script and see how long it actually takes to change channels and then use this as the timeout value for the script.

For example my dreambox only takes 1 second to change channels but then takes about 4-5 seconds to actually start sending the video stream.

Regards
Ian Dobson

---

### Post by phroman on 2011-05-06
For reference, when calling the script from the command line, or using the actual direct tv remote, it takes 3 seconds to change channels.

In the backend, with the timeout set to 0 seconds, it takes:

Main menu to live tv: 9 seconds

While watching live tv, time to change channels: 9 seconds

While watching the actual direct-tv input on my tv, but changing the channel with my mythtv remote, it takes 6 seconds to change channels and get a picture.  I'm thinking this is pretty close to as fast as it's going to get.  I'd certainly love to hear from anyone who's system is faster and how they did it of course.  


Any time added to the timeout in the backend just adds more time to get to live tv or change the channel.  But there are definitely differences from my 9.04 Mythbuntu.  The HDPVR has a blue light that comes on when watching live tv or recording.  In 10.04 when you go from the main menu to watching live tv or change a channel, the blue light comes on instantly for a second, then goes off, then comes on again, then you get a picture, 9.04 never did that.  Anyone have faster times using an HDPVR?  

I now have one less cable cluttering up the back of my entertainment center.


Ian, as always, thanks for your help.

---

### Post by salvo84 on 2012-02-28
I am planning on doing a Mythbuntu setup in the near future and was wondering the main purpose of controlling the DirecTV box.

Are you using it to change the channel for your PVR? or are you actually watching TV through your Mythbuntu box and using it to change the channel as you would if you were using just the DirecTV box?

I guess what I am trying to get at is how you have the DirecTV box 'integrated' or hooked up to your Mythbuntu box.

Is it possible to use the DirecTV DVR so you don't have to setup your own PVR?

---

### Post by salvo84 on 2012-11-04
anyone have some insight?

---

### Post by lionsnob on 2012-11-04
> **salvo84 said:**
> I am planning on doing a Mythbuntu setup in the near future and was wondering the main purpose of controlling the DirecTV box.

Are you using it to change the channel for your PVR? or are you actually watching TV through your Mythbuntu box and using it to change the channel as you would if you were using just the DirecTV box?

I guess what I am trying to get at is how you have the DirecTV box 'integrated' or hooked up to your Mythbuntu box.

Is it possible to use the DirecTV DVR so you don't have to setup your own PVR?

Hi -

This script just changes the channel on the DirecTV receiver, nothing more.  You don't have to use MythTV to use this script, although that's why I wrote it.

Thanks!

---

