---
title: "MLB.TV Nexdef Plug-In for Ubuntu???"
date: 2010-03-31
forum: Multimedia Software
---

### Post by SolitaryMan1941 on 2010-03-31
I'm having substantial issues installing the mlbviewer so... I'm giving up and going back to Firefox. I want to be able to watch mlb.tv in high definition. With Windows OS the nexdef plug-in works great but I don't have Windows OS on my HTPC. I can watch games on Ubuntu through mlb.tv via Firefox but not in HD because there is no Linux based nexdef plug-in. Any and all ideas are appreciated.

---

### Post by cwk on 2010-04-01
Last year, you could grab the autobahn.jar file from the mac version of nexdef or from [http://www.mlb.com/nexdef-jars/](http://www.mlb.com/nexdef-jars/), and run it that way. It looks like they updated to a new version of nexdef yesterday or today though, and it's no longer working.

I assume someone will figure it out soon.

---

### Post by NoVista on 2010-04-03
Unfortunately for us MLB/Ubuntuees, every new baseball season starts out with how to get MLB to work, immediately followed by a new Ubuntu Distro release, with perhaps MLB not working again.

---

### Post by PowerRanger on 2010-04-06
Seems I remember mounting the .dmg from the mac installer link  on the mlb download center page, and extracting the .jar from there.  I don't have time now to try, maybe by next weekend I'll get a chance to try...

---

### Post by karlrove on 2010-04-09
> **cwk said:**
> Last year, you could grab the autobahn.jar file from the mac version of nexdef or from [http://www.mlb.com/nexdef-jars/](http://www.mlb.com/nexdef-jars/), and run it that way. It looks like they updated to a new version of nexdef yesterday or today though, and it's no longer working.

I assume someone will figure it out soon.

The new jar is now there.

---

### Post by NoVista on 2010-04-09
Yes, Boxee IS a nice alternative.

---

### Post by snowpine on 2010-04-09
Mlbviewer is nice. Boxee is a good alternative too. :)

---

### Post by ccrs8 on 2010-04-19
I don't even NEED high def - I just want MLB.TV to play standard def correctly.  Currently in Firefox it is very choppy.  Actually, choppy would indicate that the audio or video skips/pauses - that is not the case.  The game audio and video seems to be delivered correctly, but weird flash-based menus and text are always popping up over the game.  This does not happen on the windows computer I use at work.

I used mlbviewer in 2008 when MLB moved to Silverlight and it was awesome.  Last year MLB went back to Flash so I went back to Firefox and it was tolerable.  I didn't realize until researching yesterday that mlbviewer eventually was fixed to work for last season (and with high def, too!).  Now I can't get Firefox to work without the above described issue, and I can't get mlbviewer to work, either.

Does anyone have a solution re: the Firefox issue, or possibly could help me get mlbviewer to work again?  I got the latest code from svn (0.1alpha12) but every time I launch it I get an error saying it has a problem parsing the listings page.  My credentials are correct in the config file.  I saw a very large thread in the Fedora forums and tried a few things recommended there, but could not get things working.

Any help would be greatly appreciated.

---

### Post by snowpine on 2010-04-19
> **ccrs8 said:**
> I don't even NEED high def - I just want MLB.TV to play standard def correctly.  Currently in Firefox it is very choppy.  Actually, choppy would indicate that the audio or video skips/pauses - that is not the case.  The game audio and video seems to be delivered correctly, but weird flash-based menus and text are always popping up over the game.  This does not happen on the windows computer I use at work.

I used mlbviewer in 2008 when MLB moved to Silverlight and it was awesome.  Last year MLB went back to Flash so I went back to Firefox and it was tolerable.  I didn't realize until researching yesterday that mlbviewer eventually was fixed to work for last season (and with high def, too!).  Now I can't get Firefox to work without the above described issue, and I can't get mlbviewer to work, either.

Does anyone have a solution re: the Firefox issue, or possibly could help me get mlbviewer to work again?  I got the latest code from svn (0.1alpha12) but every time I launch it I get an error saying it has a problem parsing the listings page.  My credentials are correct in the config file.  I saw a very large thread in the Fedora forums and tried a few things recommended there, but could not get things working.

Any help would be greatly appreciated.

Definitely post your problems on the mlbviewer mega-thread over on LinuxQuestions.org. The mlbviewer developer is very helpful, and it is a good alternative to the Flash/brower method.

I've also had excellent luck with Boxee. I don't know how it works, but it is very smooth. Make sure to download the latest version.

---

### Post by ccrs8 on 2010-04-19
> **snowpine said:**
> Definitely post your problems on the mlbviewer mega-thread over on LinuxQuestions.org. The mlbviewer developer is very helpful, and it is a good alternative to the Flash/brower method.

I've also had excellent luck with Boxee. I don't know how it works, but it is very smooth. Make sure to download the latest version.

Thanks!  I just tried Boxee, and it definitely works better than Firefox/Flash.  I'd say that it is as good as Firefox/Flash last year, before all the weird issues.  At least now while I try to fiddle with and fix mlbviewer I won't have an unusable alternative.

---

### Post by okdok on 2010-06-23
> 
Re: MLB.TV Nexdef Plug-In for Ubuntu???
Quote:
Originally Posted by cwk  
Last year, you could grab the autobahn.jar file from the mac version of nexdef or from [http://www.mlb.com/nexdef-jars/](http://www.mlb.com/nexdef-jars/), and run it that way. It looks like they updated to a new version of nexdef yesterday or today though, and it's no longer working.

I assume someone will figure it out soon.
The new jar is now there.


The link to the jar file returns a 403 forbidden. Has anyone been able to access this file or have another resource to get it?

---

### Post by rbokoskijr on 2010-06-26
I got the NexDef plugin to work with firefox. I installed wine then downloaded the windows nexdef installer. You can only download the windows installer from within windows so I have attached the file I downloaded. Then ran the installer using wine. The only thing is that I need to rerun the installer every time I reboot but that take all of to 2 seconds so I can deal with that. 

Code: 

wine mlbnexdefinstall.exe

For newbies to install wine here is the code

sudo apt-get install wine

FYI I am running Ubuntu 10.04 i386

---

### Post by rbokoskijr on 2010-06-26
Sorry I was unable to attach the Windows installer download. The file is to large.

---

### Post by banosd on 2010-06-29
I used the authobahn.jar that they had for download on the mlb.com site.  There was a forum there that gave the link to it but I did not notice any difference using it.  Firefox and flash work just fine.

---

### Post by SolitaryMan1941 on 2010-06-29
I've tried running NexDef through Wine and it appears to install successfully, but I have a choppy feed with the HD setting on a 52" LCD. When I don't have the game Full Screen the picture is smooth and HD. My bandwidth is usually between 6000-9000 kbps, which is two to three times what MLB says is sufficient for HD (3000kbps); I even use their speed test to check the bandwidth. I'm at a loss on this one. Their tech may not support large TV's at this point in time or they may hate open software. I suggest we all keep bugging their tech people to create internal support for Non-Windows/Non-Apple products.

---

### Post by drs305 on 2010-07-17
For the past week or so I've been having lots of problems with Gameday Audio. Often a new window opens but then nothing happens- especially archived games. Without going into lots of specifics regarding apps/settings/etc, is anyone else in here experiencing problems with Gameday/At Bat Audio on the MLB site?

---

### Post by kweisen on 2010-07-18
> **drs305 said:**
> For the past week or so I've been having lots of problems with Gameday Audio. Often a new window opens but then nothing happens- especially archived games. Without going into lots of specifics regarding apps/settings/etc, is anyone else in here experiencing problems with Gameday/At Bat Audio on the MLB site?

I haven't had any issues with Gameday audio, although I don't think I've used it hear archived games the last couple of weeks - only active games.  Also, I almost always use the Alternative Audio selection

However, I just tried it using Gameday/At bat - archived game from yesterday and it worked.

---

### Post by Detonate on 2010-07-18
I have no problems with Gameday Audio Lite. I listen to it every day the Braves are playing.  I sure miss the old days when almost all of their games were on TBS.

The only glitch I have is that, occasionally it will drop the broadcast in the middle of the game, but I think that is being caused by me visiting a web site with flash content and that web site stealing flash.  Since I installed Flashblock I don't seem to have the problem as often.

---

### Post by drs305 on 2010-07-18
> **kweisen said:**
> However, I just tried it using Gameday/At bat - archived game from yesterday and it worked.

Thanks. I cannot get archived games to play except from the Alternate Audio section, which only allows the full stream and no advancement. 

Now I'll have to figure out if this is 64-bit related or not....  ](*,)

---

### Post by bob_w on 2010-09-21
> **rbokoskijr said:**
> I got the NexDef plugin to work with firefox. I installed wine then downloaded the windows nexdef installer. You can only download the windows installer from within windows so I have attached the file I downloaded. Then ran the installer using wine. The only thing is that I need to rerun the installer every time I reboot but that take all of to 2 seconds so I can deal with that. 

Code: 

wine mlbnexdefinstall.exe

For newbies to install wine here is the code

sudo apt-get install wine

FYI I am running Ubuntu 10.04 i386

I'm a newbie... were do I put the mlbnexdefinstall.exe file?
Thanks 
Bob

---

### Post by bob_w on 2010-09-21
> **SolitaryMan1941 said:**
> I've tried running NexDef through Wine and it appears to install successfully, but I have a choppy feed with the HD setting on a 52" LCD. When I don't have the game Full Screen the picture is smooth and HD. My bandwidth is usually between 6000-9000 kbps, which is two to three times what MLB says is sufficient for HD (3000kbps); I even use their speed test to check the bandwidth. I'm at a loss on this one. Their tech may not support large TV's at this point in time or they may hate open software. I suggest we all keep bugging their tech people to create internal support for Non-Windows/Non-Apple products.

I had the same problem when using Windows XP... there test said I had enough speed, but after awhile in HD mode it would switch to standard mode. I just stopped using the HD mode... since 99% of the time I didn't use the special functions and if I didn't catch the beginning of the game I watched the archive.

---

### Post by bob_w on 2010-09-21
> **bob_w said:**
> I'm a newbie... were do I put the mlbnexdefinstall.exe file?
Thanks 
Bob

I've found the answer, no need to reply.

---

### Post by eival on 2011-03-31
> **cwk said:**
> Last year, you could grab the autobahn.jar file from the mac version of nexdef or from [http://www.mlb.com/nexdef-jars/](http://www.mlb.com/nexdef-jars/), and run it that way. It looks like they updated to a new version of nexdef yesterday or today though, and it's no longer working.

I assume someone will figure it out soon.

does anyone have this working for the new 2011 season?

cause when i run the file in the terminal it just hangs after this 

```
18:55:06.212 EVENT  Starting Jetty/4.2.x
18:55:06.228 EVENT  Started HttpContext[/protected]
18:55:06.228 EVENT  Started HttpContext[/]
18:55:06.228 EVENT  Started HttpContext[/]
18:55:06.230 EVENT  Started SocketListener on 127.0.0.1:8001
18:55:06.230 EVENT  Started org.mortbay.http.HttpServer@765a16

```

and i still cant access the HD feeds on mlb.tv for todays opening day games

is there something else i have to do?

---

### Post by Detonate on 2011-03-31
I watched the Braves beat the Nationals today.  Opened with flash in FF4, (Minefield) Ubuntu 10.10, 64 bit.  It took it a while to start, but after that it played fine.  Getting a Roku box next week so I can watch it on the big screen in the living room.

---

### Post by eival on 2011-03-31
actually im watching the Angels an Royals game LIVE and theres 3 quality levels one of which is HD , but when i was watching the replay of the Yankees game which wasnt live, they only give me 2 quality options, neither is HD but the image was still very good compared to the NBA League Pass which i also have and also doesnt officially support linux so i cant access the "octoshape" features which basically claims the same higher quality features that "nexdef" does

so i guess the nexdef isnt really necessary.

---

### Post by drs305 on 2011-03-31
I don't have a video subscription but was able to watch the free broadcasts with Flash on my 64-bit system. 

The only hitch was as the blue baseball diamond appeared and the white symbol moved between the bases, sometimes it would not progress past third base. If it stopped there, it wouldn't load.

I can delete the mlb folder in ~/.macromedia/Flash_Player/#SharedObjects/<somename>/mlb.mlb.com, then refresh the page and the white symbol runs all the bases and the video loads.

If any of this makes sense, you are a true baseball fan.

---

### Post by eival on 2011-03-31
> **Detonate said:**
>  Getting a Roku box next week so I can watch it on the big screen in the living room.


oh crap, i forgot i had one of those :P

syncing it now, gonna test it out.


edit- okay this is definitely better, full HD, even on the finished games

oh wow, Roku now has NBA league pass too!

---

### Post by eival on 2011-04-04
okay i actually figured out how to get the plugin to work, i run the terminal code then restart the browser and the plugin test on mlb.com shows its running, but its an older version.

when i try to download/install the newest one, nothing ever pops up, does anyone know how to download the latest version?

---

### Post by Tevla on 2011-04-14
Firstly, the download link may not work for you, as it is wonky JavaScript. The download link is: [http://mlb.mlb.com/media/player/nexdef/v2011_122/mlbnexdefinstall.dmg](http://mlb.mlb.com/media/player/nexdef/v2011_122/mlbnexdefinstall.dmg) (As of 4/14/2011)

The following commands are how I did it:

1. Navigate to your Downloads folder.
2. Do the following commands; if you don't have the programs, install them.
```
dmg2img mlbnexdefinstall.dmg
sudo modprobe hfsplus
mount -t hfsplus -o loop mlbnexdefinstall.img /mnt
cp /mnt/MLB.TV\ NexDef\ Plug-in.pkg/Contents/Archive.pax.gz .
gzip -d Archive.pax.gz
pax -r < Archive.pax
cd Library/Application Support/Swarmcast/lib 
java -Xmx128m -jar ./autobahn.jar
```It works for me, so I hope if works for you! Let it run in Terminal while your MLB.TV is running. 

Good luck. Go Cubs.

---

### Post by thedaver on 2011-04-15
So I've got the mlbnexdefinstall.exe from my windows install for 2011 spring training on my ubuntu 10.10 box with wine installed from ubuntu's repos.

In my linux GUI desktop - with no other applications running, no browser, etc. - I open the Terminal application and type 'wine mlbnexdefinstall.exe' which executes the nexdef installer without error.  The installer ends with one more line of wine information back to the terminal window and returns me to the Terminal command prompt.  Nothing more happens.  Using 'ps waux', I can definitely see some new mlb- and wine-related processes running.  But, as I say, no new windows open up, nothing about mlb.tv.

I had somehow expected the nexdef mlb.tv to fire up a window of its own and start the mlb experience.  Did I not go far enough by opening a (linux, not wine) firefox instance and try to browse to mlb's 'view/watch' page to get mlb.tv started???

I have a little confusion figuring out how I get the experience started on linux, but no errors so far.     

If this is going down a rat hole, I can try the previous post for the direct java launch.

Please advise!  Thanks.  (Eamus Catuli)

---

### Post by eival on 2011-04-15
> **Tevla said:**
> Firstly, the download link may not work for you, as it is wonky JavaScript. The download link is: [http://mlb.mlb.com/media/player/nexdef/v2011_122/mlbnexdefinstall.dmg](http://mlb.mlb.com/media/player/nexdef/v2011_122/mlbnexdefinstall.dmg) (As of 4/14/2011)

The following commands are how I did it:

1. Navigate to your Downloads folder.
2. Do the following commands; if you don't have the programs, install them.
```
dmg2img mlbnexdefinstall.dmg
sudo modprobe hfsplus
mount -t hfsplus -o loop mlbnexdefinstall.img /mnt
cp /mnt/MLB.TV\ NexDef\ Plug-in.pkg/Contents/Archive.pax.gz .
gzip -d Archive.pax.gz
pax -r < Archive.pax
cd Library/Application Support/Swarmcast/lib 
java -Xmx128m -jar ./autobahn.jar
```It works for me, so I hope if works for you! Let it run in Terminal while your MLB.TV is running. 

Good luck. Go Cubs.



KICK *** MAN it works!!!

[http://img842.imageshack.us/img842/9379/screenshot1fz.jpg](http://img842.imageshack.us/img842/9379/screenshot1fz.jpg)

theres a screen shot showing i have access to all the HD feeds, i cant wait till the games start later today to try out the live DVR, damn this is awesome.

yo, do you know how to get the octoshape plugin for the nba league pass to work on linux too?

its a lil different cause they actually dont even have a place to download the app, it just automatically pops up if you're running windows and possibly mac's, but its NOT the same plugin that you get from octoshape.com its specifically distrubted thru nba.com

even tho the season is over, thats the only other sports package which i use that has these limited features unless you have the "special plugin"


but these plugins are complete crap anyways and really unnecessary, cause i get the NFL Rewind too which gives you all these features, including 3000kbps highest HD feed and dvr features an everything right with the default adobe flash player, no other plugins needed.

but thanx for finding the 2011 nexdef.

---

### Post by eival on 2011-04-15
oh man that synced radio and tv feature is gonna be awesome when the yankees play on FOX or ESPN on the weekends i no longer have to listen to the idiot announcers who dont even know anything about the teams and just mumble generic banter

---

### Post by Tevla on 2011-04-15
Thedaver: I would probably advise against using WINE for this purpose, unless you have a really compelling reason to do so. It looks to me like Nexdef is a stream sniffer, and waits to be activated once the MLB.TV stream kicks off. Moreover, its a background process, so even on Windows it won't do anything tangible when you run it. I don't know if two instances of WINE have full awareness of the other, or if they exist separately.

I would suggest using what I posted; it really is quite easy, and if you get a program not found just use sudo apt-get install; their packages are named the same as their programs. Plus, the NexDef plugin uses a lot of CPU, so it is probably superior to run it natively in Linux. If Pat Hughes and Keith Moreland knew the lengths we go to to hear them synched to TV, I'm sure they'd be impressed.

Eival: I am not sure that the Octoshape plugin is different from the one on the NBA website, but it seems that using it with Linux is not the same. You have to tell Octoshape what stream you want it to run, then which will then open your preferred media player and not within the browser.  I found this information [here]("http://www.octoshape.com/index.php?page=get_octo/faq&page=get_octo/faq&faqtype=Linux"). Determining the webstream address can be very difficult for these league websites, and sometimes do not allow multiple instances. I think these guys are on the right track [here]("http://ubuntuforums.org/showthread.php?t=737088"). I don't subscribe to NBA LP, but I usually use the free trial in October, so perhaps I will revisit it then.

Good luck (but not to the Yankees :D)!

---

### Post by eival on 2011-04-15
> **Tevla said:**
> 
Eival: I am not sure that the Octoshape plugin is different from the one on the NBA website, but it seems that using it with Linux is not the same. You have to tell Octoshape what stream you want it to run, then which will then open your preferred media player and not within the browser.  I found this information [here]("http://www.octoshape.com/index.php?page=get_octo/faq&page=get_octo/faq&faqtype=Linux"). Determining the webstream address can be very difficult for these league websites, and sometimes do not allow multiple instances. I think these guys are on the right track [here]("http://ubuntuforums.org/showthread.php?t=737088"). I don't subscribe to NBA LP, but I usually use the free trial in October, so perhaps I will revisit it then.

Good luck (but not to the Yankees :D)!

na i actually emailed nba and octoshape at the beginning of the NBA season last NOV and they told me that the nba league pass plugin is different from the octoshape player from octoshape.com

the problem is, theres no place to actually manually download it, its just one of those automatic plugin checks that nba.com does but if you're not on windows or mac it never comes up.

unless someone who has a mac and league pass would be able to locate a similar jar file then it should be similar to use like this NEXDEF.

but i as i said earlier ITT, i found out that the Roku player now has League Pass streamning, so i can stream the games in HD plus it lets me have all the live dvr controls, so its not that big of a deal.

i prolly wont get league pass anyways cause their archived games blackout restrictions are really bad compared to MLB.TV, you cant rewatch ANY regional games, and none of the ABC/ESPN/TNT and those fan night games on NBA TV as well as any other random schedualed NBA TV games are permantly blackedout, which is like 50% of the season and 99% of the best games each year.

not to mention on top of all this they charge close to $200, MLB.TV is only $100 with 2x as many games and no blackouts an a better interface.

---

### Post by chuck_d on 2011-04-15
> **Tevla said:**
> Firstly, the download link may not work for you, as it is wonky JavaScript. The download link is: [http://mlb.mlb.com/media/player/nexdef/v2011_122/mlbnexdefinstall.dmg](http://mlb.mlb.com/media/player/nexdef/v2011_122/mlbnexdefinstall.dmg) (As of 4/14/2011)

The following commands are how I did it:

1. Navigate to your Downloads folder.
2. Do the following commands; if you don't have the programs, install them.
```
dmg2img mlbnexdefinstall.dmg
sudo modprobe hfsplus
mount -t hfsplus -o loop mlbnexdefinstall.img /mnt
cp /mnt/MLB.TV\ NexDef\ Plug-in.pkg/Contents/Archive.pax.gz .
gzip -d Archive.pax.gz
pax -r < Archive.pax
cd Library/Application Support/Swarmcast/lib 
java -Xmx128m -jar ./autobahn.jar
```It works for me, so I hope if works for you! Let it run in Terminal while your MLB.TV is running. 

Good luck. Go Cubs.

If I could pay you for this information I would.  Instead I'll just root for the Cubs when they aren't playing the Red Sox.  Cheers!

---

### Post by thaumielx72 on 2011-04-16
All was well until this:

$ cd Library/Application Support/Swarmcast/lib
bash: cd: Library/Application: No such file or directory
$ 

What am I missing?

Thanx in advance.  (Can't wait to see the Phillies win in High Def...)
:popcorn:

---

### Post by eival on 2011-04-16
> **thaumielx72 said:**
> All was well until this:

$ cd Library/Application Support/Swarmcast/lib
bash: cd: Library/Application: No such file or directory
$ 

What am I missing?

Thanx in advance.  (Can't wait to see the Phillies win in High Def...)
:popcorn:


just go to Places > Home Folder > Library > Application Support > Swarmcast > lib > 

then paste this code into the terminal but dont hit enter  

```
java -Xmx128m -jar
```
make sure to add a space at the end then drag the autobahn.jar file into the terminal and hit enter.

plus you can move that autobahn.jar file to your desktop for quicker access in the future if you want.

EDIT- you may have to restart your browser for the plugin to work

---

### Post by eival on 2011-04-18
after using the plugin the last few days i must say i notice theres a few issues.

first, i can no longer run mlb.tv in more than 1 browser window, it crashes the flash plugin in the first window every time, the 2nd window game will keep going tho. this even happens when i use 2 different browsers (chrome/firefox/opera) ive never seen the flash plugin be effected by the other browser cause ive flash crash in the past for different reasons but the other browser still works.

i can still open mlb.tv in multiple windows when nexdef isnt running. (if you dont understand what i mean, you can use the single player "mosaic view" of 2 or 4 games, but i like to open 2-4 browser windows and watch 2-4 games in the larger default size on my desktop it fits perfectly on my 20" 1080p monitor)

also another issue i noticed, if im streaming a game in nexdef then while browsing on the internet in a seperate browser(i use Chrome for the games an FF for my everyday browser) if a site has any streaming flash content, sometimes it resets the game back to the beginning and ive even seen it switch to the normal non-nexdef feed. although it could just be that the nexdef being disabled is what also causes the stream to start back at the beginning.



has anyone else noticed these issues?


i guess i should email mlb about it too but when they find out im running it in linux they'll probably just give me the generic, "we cant provide help since our plugin doesnt officially support linux"

---

### Post by eival on 2011-05-09
todays update for Chrome(11.0.696.65) fixed the issue of multiple windows running games with the nexdef plugin crashing.
:popcorn:

[http://yfrog.com/mqscreenshot7cj](http://yfrog.com/mqscreenshot7cj)

---

### Post by erans on 2011-05-29
Thanks so much for the Nexdef fix. I have noticed one problem. I have a laptop with an i3 and Intel HD 3000 graphics. On Win7, Nexdef works very well. On 11.04, Nexdef is very choppy and, IMO, unwatchable. I was wondering if anyone else was having performance issues with the Nexdef switch, or if it could be a problem with the Intel HD 3000 drivers?

---

### Post by eival on 2011-06-08
> **erans said:**
> Thanks so much for the Nexdef fix. I have noticed one problem. I have a laptop with an i3 and Intel HD 3000 graphics. On Win7, Nexdef works very well. On 11.04, Nexdef is very choppy and, IMO, unwatchable. I was wondering if anyone else was having performance issues with the Nexdef switch, or if it could be a problem with the Intel HD 3000 drivers?


well it could be an 11.04 issue, i would advice sticking with the LTS cause its more stable plus they have a 1 year overlap of support after the next LTS comes out so most of the kinks are worked out by the time you're finally forced to upgrade.

ive been using 10.4 and havent noticed those issues.

i also have an intergraded Intel GPU but as far as im aware they dont support Linux and the alternative drivers they endorse seemed way to complicated to install compared to when i use to have an Nvidia GPU so i never bothered, ive been using the default Ubuntu drivers and havent had any issues so far

also it could be the browser you're using, im assuming 11.04 probably uses a newer version of Firefox which could still have bugs that FF 3.6 doesnt

i also know that the latest version of Flash had some compatibility issues with Linux, as i stated in my thread about Stickam, seeing as how i downgraded and havent really been watchign alotta baseball the last few weeks i havent been able to test it to know if it had issues with mlb.tv too

u could try downgrading flash back to the 10.2 release, just google "older flash version" an you'll see the official adobe page. and use the flash-aid firefox addon to help rollback the driver.

---

### Post by eival on 2012-02-25
bumping this since the new season just around the corner, just wanted to know if a new version of the plugin has been released and if anyone knows the URL for it

if not keep us posted:popcorn:

---

### Post by snowpine on 2012-02-26
> **eival said:**
> bumping this since the new season just around the corner, just wanted to know if a new version of the plugin has been released and if anyone knows the URL for it

if not keep us posted:popcorn:

Subscribe to this thread to get the latest news: [http://www.linuxquestions.org/questions/fedora-35/mlb-tv-in-linux-432479/](http://www.linuxquestions.org/questions/fedora-35/mlb-tv-in-linux-432479/)

I would not expect a new version of the plugin until after spring training. If you set up svn, then you can easily upgrade mlbviewer throughout the season.

---

