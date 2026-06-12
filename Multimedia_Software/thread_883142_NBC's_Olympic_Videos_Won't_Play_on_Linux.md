---
title: "NBC's Olympic Videos Won't Play on Linux"
date: 2008-08-07
forum: Multimedia Software
---

### Post by TCWriter on 2008-08-07
I was prowling NBC's sizable Olympic Web site when I got the dreaded notice: while Firefox is supported in Mac and Windoze, Linux versions weren't supported.

This means the considerable amount of online video available to other users is out of reach of the Linux crowd.

Any ideas for circumventing this? (I'm running the latest Ubuntu and Firefox).

[IMG]http://chandlerwrites.com/images/nbcscreen.png[/IMG]

Oops. Prior search missed this - another thread on the same subject in the cafe. Note the fact they didn't find a workaround either...

[http://ubuntuforums.org/showthread.php?t=881084&highlight=NBC](http://ubuntuforums.org/showthread.php?t=881084&highlight=NBC)

[B]UPDATE: Partial Solution Found
[/B]
Thanks to the work of several members, we now have a partial solution; a Python script that searches out the Windows Media Player video on the NBC-Olympics Web site: 

[http://ubuntuforums.org/showpost.php?p=5574835&postcount=54](http://ubuntuforums.org/showpost.php?p=5574835&postcount=54)

Many still report sound-related issues, but at least the videos are playing. I've made as many overtures as possible to NBC and MS in the hopes they'll make changes and offer Linux users the exact same access to videos given Windows users who don't wish to install the Silverlight plugin. 

**ANOTHER UPDATE: This Seems to Work For Most**

Progress has been made to the point that I sent my wife's Windows laptop back to her workplace: This post seems to have found the most reliable method for watching streaming video on Ubuntu Linux:

[http://ubuntuforums.org/showpost.php?p=5596248&postcount=84](http://ubuntuforums.org/showpost.php?p=5596248&postcount=84)

**ANOTHER UPDATE: Olympics Over, I'm calling this a win**

The Olympics officially ended last night, but I'm still watching video (3,000 meter women's steeplechase going now - a race I highly recommend). It wasn't perhaps the easiest video stream to get, but I really appreciate everyone's help in arriving at a couple useful solutions.

Great stuff, and a good example of the power of community.

Thanks to everyone who has contributed.

---

### Post by logos34 on 2008-08-07
FF add-on User Agent Switcher set to 'IE' gets me past the notice screen, but still won't play.

I'm downloading Safari for windows right now...gonna try it on wine, maybe it will work.

---

### Post by MedellinManDem on 2008-08-07
I was wondering this as well.

---

### Post by TCWriter on 2008-08-07
I had no trouble playing video from NBC's "regular" Web site, so there's damned few excuses why they shouldn't support Linux on the Olympic site.

Interestingly, when you register for the site, NBC's Terms of Service specifically allow them to:

[INDENT]ii. restricting the availability and/or scope of the Service or restricting the availability of certain content to certain platforms (i.e., computer types and operating systems), or to certain users (i.e. streaming live and rewind video coverage may only be accessed by users who are customers of NBCOlympics cable and satellite distribution partners);  [/INDENT]

Why would you even bother to spell that out? Anyway, they'll get the whiny complaint email from me (which they'll ignore). Still, you wonder why they'd want to kiss off 2%-3% of the desktops...

---

### Post by mknepher on 2008-08-08
The streaming uses Silverlight. All of the articles I've seen on the online coverage also say that once the Olympics begin (i.e., a few hours from now), streaming will be limited to Vista users. Microsoft apparently has a partnership with NBC.

---

### Post by TCWriter on 2008-08-08
This whole issue does center around Microsoft's Silverlight, which I believe is available for Macs.

Amusingly, the MS Web site ignores the reality of the situation with a lot of corporatespeak: 

> Microsoft® Silverlight&#8482; is a cross-browser, cross-platform, and cross-device plug-in for delivering the next generation of media experiences and rich interactive applications for the Web.

"Cross platform" - as long as it isn't Linux (or a non-Intel Mac).

[IMG]http://chandlerwrites.com/images/sliverlightalert.png[/IMG]

There is a Linux version in the works by Novell (Moonlight), though it appears to be far from ready.

Interestingly, it's not all love for Silverlight on the MLB site:

[http://www.crn.com/software/209903322](http://www.crn.com/software/209903322)

Thanks Microsoft (again). I've largely given up on your junky software anyway, but rest assured I'll never buy anything from you kids again.

---

### Post by MaindotC on 2008-08-08
I'm seeing what I can dig up w/ Sopcast.  [http://www.myp2pforum.eu/watch-beijing-2008-live/](http://www.myp2pforum.eu/watch-beijing-2008-live/)

---

### Post by MaindotC on 2008-08-08
Looks like this stream is live - not sure what language it is :(

[http://www.justin.tv/live24_2](http://www.justin.tv/live24_2)

---

### Post by MaindotC on 2008-08-08
Ok, I dunno what sopcast is going to give you but what I did was just watch it on XP in Virtual Box.  Right now I'm watching women's basketball Mali vs New Zealand.  I know that's not native but it uses Msoft's blasted Silverlight and looks pretty nice.  I'm sure you can try sopcast as well as streaming channels on ustream, mogulus, or justin.tv, but a VM seems to provide the best solution with the option to choose which event you want to watch.  And there's no commentary so I don't have to hear Bob Costas ruin anything.

---

### Post by hissyfut on 2008-08-09
Once again NBC will ruin and is ruining the olympics broadcast. Right now there are interesting competitions happening, and NBC is playing the Today Show. What a load of crap.

There is no way I'm' putting the Silverlight - DRM laced - spyware crap on my computer (read the Privacy statement - the program constantly sends your computer info to microsoft and to the streaming web site - you can turn off updates, but the instructions DO NOT SAY if that will turn off sending your computer info. Plus it updates your system with fresh DRM **** = bad).

Screw Microsft and even more screw NBC for cutting off a large population of non-microshit users.
You have to ask yourself:
Why would they use this software?
Becasue they can manipulate, track, and get somewhat personal information about you. There is no other reason.

---

### Post by moore.bryan on 2008-08-09
couple things i found-out before i read this thread...
  1. all streaming on [nbcolympics.com]("http://www.nbcolympics.com/") is through the     silverlight platform.
  2. silverlight is **uninstallable** through wine.
  3. video won't play even in windows safari.

cross-platform; right! :mad:

---

### Post by stevek123 on 2008-08-09
NBC's ties to M$ **stink**. I did follow strAlan's link to justin.tv and found a couple of events that could be viewed there last night. I found another link in a related ubuntu thread that offered 36 streams from europe but it will require setting up a bogus IP address - and I'm a noob at ubuntu and not fluent enuff to do it right. FWIW - I still maintain an XP unit (pirated OS :) ) that my family uses (until I get my Linux experience down and can eliminate M$ completely) and tried to get NBC's streams successfully. It wanted to install Silverstone but I told it to play without it _and it did_. Disappointing I had to go up and use that system but I did get Olympics to play on my XP computer....  If anyone can explain how to do the IP address thing as a temporary setup, I'd be willing to try...

---

### Post by MaindotC on 2008-08-09
I think the thing with the bogus IP address is something called a proxy. I guess some sites won't let you view their content because of the origin of your IP address, so you have to connect to a proxy server that is located in the area that the website will allow (usually in the same country which is broadcasting) and then the proxy server will connect to the website that will show you the stream.  You enter the proxy server address in Firefox by clicking Edit -> Preferences -> Advanced -> Network and click the "Settings" tab.  There are also millions of tutorials you can find by googling "firefox proxy server" or any variation.  In my experience I've found most of the proxy servers are already in extremely high use and don't send you the stream fast enough for decent video, but hopefully you'll have better luck.  If not, keep trying Sopcast.

---

### Post by TCWriter on 2008-08-09
After mucking with all the alternatives (I'm not a techie - just a writer who likes Linux for its speed and reliability), I'm reduced to asking my wife to bring an extra XP laptop home from work. 

Thanks again, Microsoft. We didn't *really* require more proof that an open source alternative is a necessity, but you provided it anyway.

---

### Post by Master Chief on 2008-08-09
I installed Moonlight and tried:

```
javascript:alert(navigator.plugins["Silverlight Plug-In"].description);
```

Which returns: "[COLOR="Red"]1.0.30401.0 (compatible). Novell <a href="http://www.mono-project.com/Moonlight">Moonlight</a> 0.7 is Mono's Free/Open Source implementation of Silverlight.[/COLOR]"

instead of the usual: "[COLOR="Red"]2.0.30523.8[/COLOR]" on WindowsXP.  This in combination with:

```
var actualVer = plugin.description;
if ( actualVer === "1.0.30226.2")
actualVer = "2.0.30226.2";
var actualVerArray =actualVer.split(".");
while ( actualVerArray.length > 3)
```

in: [http://www.nbcolympics.com/components/script/fundamental.js](http://www.nbcolympics.com/components/script/fundamental.js)
makes it break;

Oh yes, the User Agent is the easy part, but I'm pretty sure that a small GreaseMonkey script can help out here.

---

### Post by tamoneya on 2008-08-09
I ran xp in virtual box and I still couldnt get their sit to work.  the silverlight installer kept saying my browser/OS configuration wasnt supported.  I had IE7, Firefox.  I then pulled out the vista CD and key that I got with my laptop and installed it into virtual box.  Only then did I get their site working.

---

### Post by Master Chief on 2008-08-09
> **tamoneya said:**
> I ran xp in virtual box and I still couldnt get their sit to work.  the silverlight installer kept saying my browser/OS configuration wasnt supported...

Oh?  It works here with WindowsXP/SP3 in VirtualBox v1.6.2  
Silverlight even works with SeaMonkey (the Mozilla Firefox sibling).

---

### Post by tamoneya on 2008-08-09
> **Master Chief said:**
> Oh?  It works here with WindowsXP/SP3 in VirtualBox v1.6.2  
Silverlight even works with SeaMonkey (the Mozilla Firefox sibling).

Maybe it is because you are SP3.  I didnt feel like doing upgrades for 10 hours.

---

### Post by phrostbyte on 2008-08-09
edit

---

### Post by phrostbyte on 2008-08-09
So it seems there are MMS streams available. 

Unfortunately, the solution is buried in one of these scripts:

[videoplayer.js]("http://www.nbcolympics.com/components/script/videoplayer.js")
[master.js]("http://www.nbcolympics.com/components/script/master.js")
[fundamental.js]("http://www.nbcolympics.com/components/script/fundamental.js")

These scripts are very complicated and crunched up to save bandwidth. But I think if we can isolate the MMS stream URL we can get it to play in VLC or MPlayer.

---

### Post by mikeric on 2008-08-09
This Sucks, i also noticed a few radio stations i used to listen to online have recently switched to using this too, so i cant listen to them either.

---

### Post by AR_Kozz on 2008-08-10
I posted about my own attempts getting around Silverlight, before I saw this thread... since it's already under discussion I guess I'll mention the main things here too

1) Silverlight does NOT work under Wine 1.0. When you try to use Firefox to watch under Wine, you get a message to download Silverlight, but then it won't extract. When I tried going back in time a bit to Silverlight 1.0 beta, I found out it had an expired root certificate; actually installing would have involved downloading several hundred megabytes more. That is, it's just an archive of a downloading client. The newer version shut you down without saying why. In any case, WineHQ rates Silverlight "Garbage."

2) There is a linux port of Silverlight, but it is not finished yet. Imagine Microsoft-nbc not getting it done in time for the olympics (it was expected by "mid-year.") If you want to try to get it working with Firefox, you'll have to compile it. Here's a link:

[http://www.go-mono.com/moonlight/](http://www.go-mono.com/moonlight/)

Before you get all excited note the binaries don't play video, and it's hard to compile. (I'm too tired right now to go through that frustrating process)

3) China Central Television streams its main sports network, CCTV5, over the net. It's lousy but it's live. Try this one:

mms://218.56.57.38/cctv5

Also, if anyone is good at using proxies, the Canadian Broadcasting Corporation [www.cbc.com](www.cbc.com) is also multicasting olympic sports, and they are using wmv as their format. Mplayer would work there but for me in the USA it's region-locked. I've tried using proxies but they still know I'm south of the border. If anyone in the US gets it working, please spread the good word.

Finally there is supposed to be streaming available on bbc.com, but again I can't find it. If anyone can access this with proxies or something, I'd like to know.

---

### Post by Hairy_Palms on 2008-08-10
well that sucks, at least here in the uk i can catch all the coverage using the BBC iplayer, so i guess coverage will start to pop up on torrent sites sooner or later

---

### Post by moore.bryan on 2008-08-10
> **AR_Kozz said:**
> 2) There is a linux port of Silverlight, but it is not finished yet.... Before you get all excited note the binaries don't play video, and it's hard to compile. (I'm too tired right now to go through that frustrating process)
you're preaching to the choir there... this is a *real* promising program which is a **huge** PITA to get going *if* it even compiles for you.

> 3) China Central Television streams its main sports network, CCTV5, over the net. It's lousy but it's live.
my connection is actually pretty decent... well, at least fair. doesn't let you choose what to watch, but at least it's more coverage.

> Also, if anyone is good at using proxies, the Canadian Broadcasting Corporation [www.cbc.com]("http://www.cbc.com") is also multicasting olympic sports, and they are using wmv as their format. Mplayer would work there but for me in the USA it's region-locked. I've tried using proxies but they still know I'm south of the border. If anyone in the US gets it working, please spread the good word.
cbc.com is a comic book website... ;-) try [www.cbc.ca/olympics]("http://www.cbc.ca/olympics[/url). i've tried relentlessly to get this to play nicely with ff3's [mediaplayerconnectivity]("https://addons.mozilla.org/en-US/firefox/addon/446") addon, vlc, and tor running through [foxyproxy]("https://addons.mozilla.org/en-US/firefox/addon/2464"), but no luck so far.

> Finally there is supposed to be streaming available on bbc.com, but again I can't find it. If anyone can access this with proxies or something, I'd like to know.
the bbc locks-out any ip's not in the uk and even when i've set the ip to london, i couldn't get access... i guess there's a screw loose.
;-)

---

### Post by MaindotC on 2008-08-10
It's cbc.ca, not .com and they have beautiful flash video live.  However, I can't seem to find a highlights section.  Kozz - how did you find that stream?  It seems to be danish or nordic.

---

### Post by teddmeister2 on 2008-08-10
Sorry, I made a mistake, the youtube channel I referred to previously only has Phelps's world record.

---

### Post by MaindotC on 2008-08-10
Ok scratch the CBC.  I just tried playing their live broadcast of Beach Volleyball which they're showing right now and it's not playing.  It says you need the WMP to play their blasted video.  As of right now it seems like there's only my VM solution, Sopcast, or mms streams.

---

### Post by AR_Kozz on 2008-08-10
> **strAlan said:**
> It's cbc.ca, not .com and they have beautiful flash video live.  However, I can't seem to find a highlights section.  Kozz - how did you find that stream?  It seems to be danish or nordic.

yeah, I knew that about cbc.ca. If you type enough you're bound to make an error or two 

You are correct the url I posted is in europe, it's just the particular one I used. It was a page-embedded url so Firefox doesn't try to go external with it. I need to convince Firefox that it's not supposed to use Totem for non-embedded mms, and didn't want to bother with that (I was missing the fencing). Here's the url for the page itself:

[http://www.thoughtsofanordinaryman.com/2008/08/watch-beijing-olympic-games-2008-live.html](http://www.thoughtsofanordinaryman.com/2008/08/watch-beijing-olympic-games-2008-live.html)

There's plenty of other streams of cctv5 also, non-embedded, and the cctv home page which requires you to download a client from them. I saw a number of sports-channel stream sites that include cctv5, it should be easy to find one that works with mplayer or vlc

I'm sure not everyone knew moonlight is a work-in-progress... I am gonna try and build it I think just for the hell of it... actually, maybe not

I figured the bbc.com didn't show the streams because of my location, I think every time I go there they have me pegged for a Yank... it always says "international version" for one thing... I tried using a UK proxy and they still knew I was on the wrong side of the ocean :(

strAlan, there are wmp plugins for mplayer, they're non-free though

---

### Post by Diggs808 on 2008-08-11
Cross posting this......

I have an idea that may just work...but it will take some effort and a little money on our part. Lets stage an old fashioned write in protest! Notice how all of these shows that nearly get canceled are saved by write in campaigns? In the case of Jericho...the show was saved (at least it was allowed to wrap up) by fans sending bags of nuts to the president of CBS. So lets do the same...except...lets send them a copy of our favorite distro. It won't cost much...just go online and download the ISO...burn it to a CD or two and then send it to the president of NBC along with a POLITE AND FRIENDLY letter. 

Personally I will commit to sending one of these per day until they change thier mind or the olympics end.  

Sample Letter

**Mr. Jeff Zucker **
President and Chief Executive Officer 
NBC Universal Television Group
30 Rockefeller Plaza
New York, NY 10112 
(212) 664-4444


Dear Mr Zucker,  

I have thourgholy enjoyed the Olympics so far, however we have recently discovered that the online content enjoyed by many in the United States is not available for computer users who run Linux Operating systems includling Ubuntu, Red Hat, and others. This is very disappointing for those of us who choose to use Linux. It means that we are not able to view the olympics and cheer on our team in our favorite sports. 

We are not asking for much, however what we are asking for is simple. Allow us access to the online content that many others are already enjoying. Websites outside of the US (cbc.ca and others) are broadcasting thier internet content in Flash. We respectfully ask as a community of computer users and olympic fans that you make your content available to those consumers who do not use Microsoft products. 

If you do not have the technical resources available to make this happen we offer our services as a community to make this work. 

Thank you very much for your time.

Signed,

(YOUR NAME HERE)

---

### Post by k_i_k on 2008-08-11
Actually, while it is not completely trivial, it is possible to get the live stream URLs from the NBC website without going through its terrible user interface.

I wrote a short Python script to do just that. See attached. As is, it will scan the current Tennis schedule and print the matches that are being streamed live, together with and MMS stream URL. The stream can be downloaded with mimms (apt-get install mimms) or viewed with xine or mplayer (which can also save streams with the -dumpstream option). Look inside for examples of how to change Tennis to your favorite sport. If you want to view past matches, change 'Live ' to 'Rewind ' in the script. Although, I've so far had not had much success with that.

Alas, this script will only work if you're inside the US. Try the script, modify to your heart's desire and spread the word.

---

### Post by akashiii on 2008-08-11
Hi K_I_K,

Thanks for the script ! :)

Just a quick question - I'm getting an import error below when I run your script on Ubuntu Hardy i386 on Python 2.5.2 (preinstalled on the OS). I'm a bit new here, can you tell me what I'm doing wrong, please? Is there some dependency that needs to be fulfilled here? Thank you once again in advance. Please find the CLI below -

> 
me@lenovo:~/Desktop$ python --version
Python 2.5.2

me@lenovo:~/Desktop$ python nbcsched.py
Traceback (most recent call last):
  File "nbcsched.py", line 6, in <module>
    from xml.dom.ext.reader import PyExpat
ImportError: No module named ext.reader
me@lenovo:~/Desktop$ 


---

### Post by k_i_k on 2008-08-11
Here are the python packages with 'xml' in them that I have installed. It's got to be in one of them:
```

python-libxml2
python-lxml
python-xml
```

---

### Post by Octagonal on 2008-08-11
k_i_k
That works great.  I used your script and opened up the stream in vlc... I have to say it's better than viewing it from within the browser.
Thank you.

---

### Post by globose on 2008-08-11
This seems like a really promising solution, but I'm getting the same errors even after installing the dependencies (ImportError: No module named ext.reader).  I did a lot of google searches, but I can't find a good fix.  It seems like it is relying on an older pyxml rather than python-xml.  Does anyone know how to fix this?  I'm using Hardy on a 64-bit.

I found this website that gives a fix, but I don't know how to use it: [http://debianclub.org/aggregator/sources/2?page=33](http://debianclub.org/aggregator/sources/2?page=33)

Fix/workaround:
+        sys.path.append('/usr/lib/python%s/site-packages/oldxml' % sys.version[:3])
        from xml.dom.ext.reader import HtmlLib

Where would I type this?

---

### Post by AR_Kozz on 2008-08-11
Hey thank you k_i_k for that script... looks like it works, unfortunately there's nothing on right now :(

---

### Post by k_i_k on 2008-08-11
An update. NBC also has lots of stuff recored, so you can watch something you missed when it was live. The new version scans these links too. Here's how to use it:

```
./nbcsched.py <sport> <live | rewind> <pattern>
```

<sport> is the sport you are interested (badminton, tennis, volleyball, etc)

The second argument is either "live" or "rewind" for live streams or prerecorded ones.

The third argument is matched against the description for each stream, and only the matching streams are looked up. This is useful when there are many "Rewind" links, as processing them all would take several minutes.

Spread the joy! :-)

---

### Post by ace007 on 2008-08-11
And Microsoft drives more customers to piracy...

EDIT: not referring to the script above, just in general

Could someone make a tutorial for how to use this script and open the stream in VLC?

---

### Post by k_i_k on 2008-08-11
> **ace007 said:**
> Could someone make a tutorial for how to use this script and open the stream in VLC?

Umm, ace007, run the script and feed the stream URLs to VLC or another video player. No output means no streams were found or if any were they couldn't be parsed. Some/many "Rewind" streams may not work (no idea why). Read the code for details.

---

### Post by chickendude1313 on 2008-08-11
> **globose said:**
> This seems like a really promising solution, but I'm getting the same errors even after installing the dependencies (ImportError: No module named ext.reader).  I did a lot of google searches, but I can't find a good fix.  It seems like it is relying on an older pyxml rather than python-xml.  Does anyone know how to fix this?  I'm using Hardy on a 64-bit.

I found this website that gives a fix, but I don't know how to use it: [http://debianclub.org/aggregator/sources/2?page=33](http://debianclub.org/aggregator/sources/2?page=33)

Fix/workaround:
+        sys.path.append('/usr/lib/python%s/site-packages/oldxml' % sys.version[:3])
        from xml.dom.ext.reader import HtmlLib

Where would I type this?



Yo, I figured out how to get this to work:
Change the beginning of the script to look like this:

```

import re
import sys

from sys import argv
from urllib import urlopen
sys.path.append('/usr/lib/python2.5/site-packages/oldxml')
from xml.dom import Node
from xml.dom.ext.reader import PyExpat
reader = PyExpat.Reader()

```

Basically, you have to add an import sys and then use that to append to the path. Replace the 2.5 with whatever version you have, or use that general one in the one you found.

Nice work KiK. This is excellent.

---

### Post by mnmwatkins on 2008-08-11
Great script! :) However, I seem to not get any audio on these streams.  VLC works fine on files, etc. but nothing here?  Is this the same for all?

---

### Post by AR_Kozz on 2008-08-11
Ace just open the script and edit the "nowurl" lines to whatever sport you want to watch. There's several there with all but one commented out, so you can set them up for your favorite sports and just un-comment the one you want to check.

It helps to look at the stream schedule on nbcolympics.com, so far everything that's been scheduled I've found a stream. 

There's still people making new threads about this, maybe the mods would let our hero k_i_k make a sticky or something

---

### Post by mefistofeles666 on 2008-08-11
MMM...iguess u can call me a noob cuz I don't know how to make it work

I opened the file with txt editor and changed the "+sport+" part in the pink nowurl line and put the sport 'weightlifting' and then save.

and then I open the file with vlc? or what do I do next?

---

### Post by chickendude1313 on 2008-08-12
> **mnmwatkins said:**
> Great script! :) However, I seem to not get any audio on these streams.  VLC works fine on files, etc. but nothing here?  Is this the same for all?

I too have the audio problem :(

---

### Post by blehman419 on 2008-08-12
> **chickendude1313 said:**
> I too have the audio problem :(

same here...

---

### Post by blehman419 on 2008-08-12
> **mefistofeles666 said:**
> MMM...iguess u can call me a noob cuz I don't know how to make it work

I opened the file with txt editor and changed the "+sport+" part in the pink nowurl line and put the sport 'weightlifting' and then save.

and then I open the file with vlc? or what do I do next?
First make sure the nbcsched.py is on your desktop.  Then open the terminal and type ```
cd ~/Desktop
```
Then type ```
./nbcsched.py
```

copy and paste the address that is listed in the terminal.  > mms://msftolymasxlivewm.fplive.net/msftolympicslive-live/msolympics_ENC28_high?e=1218517141&h=d6a1d723dbef7db5e5b36fc9ccb0b384&token=c3RhcnRfdGltZT0yMDA4MDgxMjA0NDkwMSZlbmRfdGltZT0yMDA4MDgxMjA0NTkwMSZkaWdlc3Q9MTg3ZmQ0MTU2ODNhNGFiZGZhZjNkMGZiMzFlMDYxOGY=
 That is what an address will look like.  It will start with mms.  Open VLC and select open network stream.  You'll see a place where you can choose http and mms link types.  Paste the address there and click ok.

---

### Post by TCWriter on 2008-08-12
Sadly, I too receive the deadly "ImportError: No module named ext.reader" reply - even after applying the code patch mentioned in an earlier post. 

Still, it's been an education.

It's a shame - I now have access to a Windows box, but it would still be far better to watch this on my Linux machines, if only for the warm glow I'd receive knowing that Microsoft would rather I didn't.

---

### Post by mefistofeles666 on 2008-08-12
odd...it says no such file or directory. and the file is on my desktop

---

### Post by AR_Kozz on 2008-08-12
Mephistofeles try:

python nbcsched.py

that always stops your pc from claiming there's nothing there... also I meant replace the name of the actual sport, not the word "sport," in the lines where it says -/tennis/-, -/badminton/-, etc. Or better use the version on page 3 where you just type arguments and can access the recordings.

So far I'm batting 1.000 on the rewinds and about .100 on the live stuff. When you get the url, the "token=" part has to be there, in the middle of about 4 lines, for it to work. I almost always get an abbreviated url that ends after 1 1/2 lines, with no token, it seems like maybe it's when I've connected there recently. 

Not sure why but I wondered if there was some sort of IP ban thing... tried using proxy connection but it produced errors from the script

---

### Post by moktor on 2008-08-12
first of all, thank you very much for the awesome script!

It works great for the most part, but I am running into an issue getting the listings for weightlifting or canoekayak.

Using the modified script that accepts arguments, attempting to return live weightlifting returns the following:
> Traceback (most recent call last):
  File "./nbcsched.py", line 107, in <module>
    nowsched = Sched(nowurl)
  File "./nbcsched.py", line 97, in __init__
    self.doc = reader.fromString(self.html) # parse html
  File "/usr/lib/python2.5/site-packages/oldxml/_xmlplus/dom/ext/reader/__init__.py", line 60, in fromString
    return self.fromStream(stream, ownerDoc)
  File "/usr/lib/python2.5/site-packages/oldxml/_xmlplus/dom/ext/reader/PyExpat.py", line 65, in fromStream
    success = self.parser.ParseFile(stream)
xml.parsers.expat.ExpatError: not well-formed (invalid token): line 1, column 258

Live canoe/kayak (canoekayak) returns a similar error:
> Traceback (most recent call last):
  File "./nbcsched.py", line 107, in <module>
    nowsched = Sched(nowurl)
  File "./nbcsched.py", line 97, in __init__
    self.doc = reader.fromString(self.html) # parse html
  File "/usr/lib/python2.5/site-packages/oldxml/_xmlplus/dom/ext/reader/__init__.py", line 60, in fromString
    return self.fromStream(stream, ownerDoc)
  File "/usr/lib/python2.5/site-packages/oldxml/_xmlplus/dom/ext/reader/PyExpat.py", line 65, in fromStream
    success = self.parser.ParseFile(stream)
xml.parsers.expat.ExpatError: not well-formed (invalid token): line 116, column 778


I wish I knew more about debugging python to see if I could find out why it is doing this.

---

### Post by blehman419 on 2008-08-12
> **TCWriter said:**
> Sadly, I too receive the deadly "ImportError: No module named ext.reader" reply - even after applying the code patch mentioned in an earlier post. 

Still, it's been an education.

It's a shame - I now have access to a Windows box, but it would still be far better to watch this on my Linux machines, if only for the warm glow I'd receive knowing that Microsoft would rather I didn't.

This is an easy fix.  I tried the patch as well, and I didn't have any luck either.  You need to install a few XML packages for python.  Open Terminal and type:```

sudo apt-get install python-libxml2
```
```
sudo apt-get install python-lxml
```
```
sudo apt-get install python-xml
```

Some of these may already be on your computer, as I already had the first, but the second and third installed and I was able to use the script with no problems after that.  

Thanks again to k_i_k !  I had faith that someone would come through.  It's gotta feel cool to author a script that could help so many people for just a short period of time.

---

### Post by TCWriter on 2008-08-12
Well, hot damn. I wasn't getting any love from my "day to day" working laptop (Dell 1720), but moved the whole shooting match over to my old desktop (freshly converted to Ubuntu).

Made all the right adjustments, and apparently the stars ran their fiery courses to the proper places, so now I'm watching the finals of the men's 50 meter pistol... sans sound.


Eventually, the sound issue will go away, and I also hasten to point out the following sad fact: 

That we're watching WMV streams on Linux boxes pretty much proves the original theory: there was no reason to exclude Linux from the streaming process outside of an apparent desire to do so. 

Great work guys - and this from a writer/Linux infant who has just recently made the switch to Linux (from Vista).

---

### Post by blehman419 on 2008-08-12
> **TCWriter said:**
> Well, hot damn. I wasn't getting any love from my "day to day" working laptop (Dell 1720), but moved the whole shooting match over to my old desktop (freshly converted to Ubuntu).

Made all the right adjustments, and apparently the stars ran their fiery courses to the proper places, so now I'm watching the finals of the men's 50 meter pistol... sans sound.


Eventually, the sound issue will go away, and I also hasten to point out the following sad fact: 

That we're watching WMV streams on Linux boxes pretty much proves the original theory: there was no reason to exclude Linux from the streaming process outside of an apparent desire to do so. 

Great work guys - and this from a writer/Linux infant who has just recently made the switch to Linux (from Vista).

I wish I could help you with the sound but I am stuck as well.  I am off to work in a few minutes, but I will be back on to try to 'crank up the sound'.  Until then, if anyone gets the sound working, don't be shy and let us know how you made the fix.  Thanks all....

---

### Post by SeanBlader on 2008-08-12
What if I wanted to see the opening ceremony video's? Also './nbcsched.py swimming rewind' came up blank, is there something I was missing there?

---

### Post by globose on 2008-08-12
Thank you so much to k_i_k for writing such a great script.  Also, thanks to chickendude 1313 for the modifications to fix the pyxml problem.  

I'm attaching the modified script (to k_i_k's post #36) for anyone else who still might be getting the error code like this:

> Traceback (most recent call last):
File "nbcsched.py", line 6, in <module>
from xml.dom.ext.reader import PyExpat
ImportError: No module named ext.reader

Don't forget to have python-libxml2 , python-lxml, and python-xml installed in Synaptic.

---

### Post by globose on 2008-08-12
> **SeanBlader said:**
> What if I wanted to see the opening ceremony video's? Also './nbcsched.py swimming rewind' came up blank, is there something I was missing there?

I think this script only works for viewing the online events listed in the pictures at [http://www.nbcolympics.com/tv_and_online_listings/index.html](http://www.nbcolympics.com/tv_and_online_listings/index.html)

I suggest using this website as a guide to determine which specific event you want to watch.

---

### Post by TCWriter on 2008-08-12
Interestingly, I ran the script ("shooting") a while ago, and watched one of the shows. 

Just now, none of them would play, and re-running the script showed new addresses for the same video segments.

Moral: Don't rely on old addresses.

---

### Post by qiepenguin on 2008-08-12
I'm confused -- some sports seem to be conspicuously absent from the schedule page ([http://www.nbcolympics.com/tv_and_online_listings/index.html](http://www.nbcolympics.com/tv_and_online_listings/index.html)) and therefore from the script results.  Where are gymnastics and swimming?

---

### Post by MaindotC on 2008-08-12
I've never seen any of the televised events shown online.  For example, Michael Phelps's swimming - it was never being streamed live and I was forced to watch it on TV and hear the idiotic commentary ruin it.  Today, Togo had its first medal won by an athlete, ever, and it was in kayaking.  This was not broadcast online.

If you want a feed of NBC or CBC, have you tried sopcast?

---

### Post by wyth on 2008-08-12
This doesn't address the problem of not being able to see anything in linux, but if you're a fan of certain sports that are getting no air time and really *really* need to see them, there's one way around this that works for me.

I already had VirtualBox installed.  I slapped on an old XP I had around in VirtualBox, and from there just got Silverlight going.  Haven't missed a thing so far.

Like I said, it's not ideal, but at least I can see the events.  If you have virtualization going, it might be worth a try, at least for the next week or so.

---

### Post by mefistofeles666 on 2008-08-12
does anyone know why weightlifting isnt appearing? I tried and gave me back

tan@sakura:~/Desktop$ python nbcsched.py weightlifting rewind
Traceback (most recent call last):
  File "nbcsched.py", line 107, in <module>
    nowsched = Sched(nowurl)
  File "nbcsched.py", line 97, in __init__
    self.doc = reader.fromString(self.html) # parse html
  File "/usr/lib/python2.5/site-packages/oldxml/_xmlplus/dom/ext/reader/__init__.py", line 60, in fromString
    return self.fromStream(stream, ownerDoc)
  File "/usr/lib/python2.5/site-packages/oldxml/_xmlplus/dom/ext/reader/PyExpat.py", line 65, in fromStream
    success = self.parser.ParseFile(stream)
xml.parsers.expat.ExpatError: not well-formed (invalid token): line 1, column 258

---

### Post by Quicksilver_Johny on 2008-08-12
> **k_i_k said:**
> Some/many "Rewind" streams may not work (no idea why). Read the code for details.
I think I know why this is happening. Some sports simply don't have rewind streams, but in those that do, the assetid attribute isn't always the simple 7 digit number that the script assumes.

Some handball examples:
Women's Group A -- Preliminaries - Match 1 is: 
[http://www.nbcolympics.com/video/player.html?assetid=](http://www.nbcolympics.com/video/player.html?assetid=)**hb1h-bj-sd01-080908-085002**&channelcode=sporthb
While Women's Group B -- Preliminaries - Match 2 is:
[http://www.nbcolympics.com/video/player.html?assetid=](http://www.nbcolympics.com/video/player.html?assetid=)**1006599**&channelcode=sporthb

You appear need to go to this URL for the first example:
[http://www.nbcolympics.com/video/modules/json/resourcedata/hb1h-bj-sd01-080908-085002/asset.html](http://www.nbcolympics.com/video/modules/json/resourcedata/hb1h-bj-sd01-080908-085002/asset.html)

I don't know the regular expression system you're using, but I think you need to find all instances of *assetid={var}&* and then parse the stream url from http://www.nbcolympics.com/video/modules/json/resourcedata/{var}/asset.html

A side note, why would you need to go to:
[http://www.nbcolympics.com/video/modules/json/resourcedata/1006/599/asset.html](http://www.nbcolympics.com/video/modules/json/resourcedata/1006/599/asset.html)
Instead of:
[http://www.nbcolympics.com/video/modules/json/resourcedata/1006599/asset.html](http://www.nbcolympics.com/video/modules/json/resourcedata/1006599/asset.html)

I hope this helps you get it working for every video soon, I'm going to be without a TV!

---

### Post by globose on 2008-08-12
I might just be superstitious, but it seems like I have to paste the link in VLC player **fast** for the video to work.  I noticed that if I use the script to search for the same criteria, the address keeps changing.

I think the sound issue might have something to do with support for WMA (specifically WMAP?), but I don't really understand this.  I have all of the necessary codecs to play WMA and WMV (though I think VLC can play these without extra packages??)  Totem can't even play video or audio (internal flow error or something like that).

---

### Post by Quicksilver_Johny on 2008-08-12
I think I've got it!
Line 29 should be
```
aidpat = r"assetid=([0-9a-zA-Z\-]+)&"
```
and line 72
```
aurl = "http://www.nbcolympics.com/video/modules/json/resourcedata/" + aid + "/asset.html"
```

This should make the script work on quite a few more events, I think all of them that are on the NBC site. (Note: some stuff just isn't on there (eg: swimming); if http://www.nbcolympics.com/{SPORTHERE}/resultsandschedules/index.html has events with "Rewind" you should get it.)

---

### Post by blehman419 on 2008-08-13
Well I've tried my best to solve the audio problem.  I am almost sure I have every codec I would ever need, but still i get:>  main decoder error: no suitable decoder module for fourcc `wmap'.
VLC probably does not support this sound or video format.

I will continue trying until I get this to work.  

The video has been working nicely tonight, even if we can't get swimming or the other events that are on the national broadcast.

---

### Post by blehman419 on 2008-08-13
Well I have some hope.  I installed Ultamatix and used it to install the w32 codecs that I thoguht I had already installed.  I also installed gxine, and ran the video in that instead.  I have sound, but it isn't in sync with the video.  It's a start I guess...

---

### Post by TCWriter on 2008-08-13
Several times last night I was streaming live video on my wife's XP laptop, but the script wouldn't find the streams. 

I'm having better luck seeing "rewind" video, but getting them to play is a hit or miss process - a good 75% of the time I get an attractive error message (featuring the Olympic rings). 

Clearly, the addresses don't last long, and I wonder if NBC/MS is now only streaming *some* of the events in the Windows Media Player format we're using.

Thanks again to everyone who's made an effort. This has been an eye opener.

---

### Post by AR_Kozz on 2008-08-13
> **Quicksilver_Johny said:**
> I think I've got it!
Line 29 should be
```
aidpat = r"assetid=([0-9a-zA-Z\-]+)&"
```
and line 72
```
aurl = "http://www.nbcolympics.com/video/modules/json/resourcedata/" + aid + "/asset.html"
```

This should make the script work on quite a few more events, I think all of them that are on the NBC site. (Note: some stuff just isn't on there (eg: swimming); if http://www.nbcolympics.com/{SPORTHERE}/resultsandschedules/index.html has events with "Rewind" you should get it.)

This might work for an intermittent issue I've been having, it's exactly the same error Moktor posted but that's on the previous page so I'll rehash it:

###@########:~/Desktop$ ./nbcsched.py archery rewind
Traceback (most recent call last):
  File "./nbcsched.py", line 104, in <module>
    nowsched = Sched(nowurl)
  File "./nbcsched.py", line 94, in __init__
    self.doc = reader.fromString(self.html) # parse html
  File "/usr/lib/python2.5/site-packages/_xmlplus/dom/ext/reader/__init__.py", line 60, in fromString
    return self.fromStream(stream, ownerDoc)
  File "/usr/lib/python2.5/site-packages/_xmlplus/dom/ext/reader/PyExpat.py", line 65, in fromStream
    success = self.parser.ParseFile(stream)
xml.parsers.expat.ExpatError: not well-formed (invalid token): line 232, column 777

I'm not good with python but after looking at the code in all the files mentioned it looks like it's getting all the url's, just failing to parse them properly, particularly from that "line 232, column 777" bit at the bottom.

This is something that comes up even for sports that work. Normally archery works for instance. But maybe they change the assetid's periodically.

It also might be helpful to modify the script to just dump the whole page of listings without parsing, then try to find the url by sight

Finally for some reason k_i_k's script .2 hangs on judo with no output or termination.

<edit> nope, didn't work for that error... may still get the other sports though, once the error goes away

---

### Post by BertP on 2008-08-14
Anyone here want to help a complete noob?     I am still running Gutsy (7.10) could that be the problem?

Here are my results:
-----------------------------
python ./nbcsched.py
Traceback (most recent call last):
  File "./nbcsched.py", line 81, in <module>
    nowsched = Sched(nowurl)
  File "./nbcsched.py", line 73, in __init__
    self.doc = reader.fromString(self.html) # parse html
  File "/usr/lib/python2.5/site-packages/_xmlplus/dom/ext/reader/__init__.py", line 60, in fromString
    return self.fromStream(stream, ownerDoc)
  File "/usr/lib/python2.5/site-packages/_xmlplus/dom/ext/reader/PyExpat.py", line 65, in fromStream
    success = self.parser.ParseFile(stream)
xml.parsers.expat.ExpatError: not well-formed (invalid token): line 961, column 791

---

### Post by TCWriter on 2008-08-14
Ohhhh, this is interesting. The script had been working (albeit not at 100%), but now it fails pretty much every time:

Traceback (most recent call last):
  File "nbcsched.py", line 107, in <module>
    nowsched = Sched(nowurl)
  File "nbcsched.py", line 97, in __init__
    self.doc = reader.fromString(self.html) # parse html
  File "/usr/lib/python2.5/site-packages/oldxml/_xmlplus/dom/ext/reader/__init__.py", line 60, in fromString
    return self.fromStream(stream, ownerDoc)
  File "/usr/lib/python2.5/site-packages/oldxml/_xmlplus/dom/ext/reader/PyExpat.py", line 65, in fromStream
    success = self.parser.ParseFile(stream)
xml.parsers.expat.ExpatError: not well-formed (invalid token): line 232, column 791

What's different between now and yesterday? Got me - and it seems to be happening with both the 2.0 and 3.0 versions of the script (my version numbers). 

Equally interestingly, all my emails to NBC and MS have generated the following replies: 

None.

To steal from Telly Savalas, "Who loves ya baby?" (Hint: it ain't those two)

---

### Post by BertP on 2008-08-14
> **TCWriter said:**
> Ohhhh, this is interesting. The script had been working (albeit not at 100%), but now it fails pretty much every time:


I just tried and the script works now.  For Judo, the prefix is "mmsh://..."
does that mean it is encrypted?

---

### Post by mathew.samuel on 2008-08-14
Just remove the h from the mmsh:// and the url works. Watching Blake/Federer now

---

### Post by TCWriter on 2008-08-14
> **mathew.samuel said:**
> Just remove the h from the mmsh:// and the url works. Watching Blake/Federer now

The script finds it, but no matter how I mess with/leave alone the URL, the stream doesn't open. Most streams don't, though I can get a few to play.

It's weird. A couple days ago the streams were working well. Now almost nothing works and this on the same machine where nothing has shifted.

Also, running the script only a few seconds apart returns different addresses for the "same" feed. 

Looks like Microsoft wins this one; I'm asking my wife to bring back the Windows laptop from work. 

Next time, Microsoft...

---

### Post by k_i_k on 2008-08-14
Hello, everyone! Another update. No new source, just tips. I see a lot of helpful people have already explained how to modify the source for your own ends. Here are some problems that I've encountered myself and seen people post here, and my solutions.

**Can't find the xml modules:** Several people have already explained how to install python xml modules or how to change the module include path in the script. Look it up earlier in this thread.

**XML not well formed:** Yeah, web designers often forget what it means for a page to be valid XHTML. Mostly this is caused by an & that should have been an &amp;. There is a function defined at the top of the script called *fixent*. My version currently reads:
```
def fixent(s):
        s = re.sub(r' & ',r' &amp; ',s)
        s = re.sub(r'<script([^>]*)>',r'<script\1><![CDATA[',s)
        s = re.sub(r'</script>',r']]></script>',s)
        return s
```
If a page craps out for you, find the part where the parser breaks (the *expat* parser should tell you the exact location) and figure out how to change that part to valid XHTML. Then insert that substitution rule into *fixent*.

**No audio:** These streams are WMV9 with wma9dmo audio codec, which is only found in the w32codecs package. If you're running a 32bit system, you're fine. If not, you either give up or follow something like the instructions over at this [thread]("http://ubuntuforums.org/showthread.php?t=62685"). Personally, I did it differently, so YMMV.

**Doesn't work for my sport:** Sorry guys. I've only really tested this with badminton. However, you might find that there is a problem with line:
```
aurl = "http://www.nbcolympics.com/video/modules/json/resourcedata/" + aid[:4] + "/" + aid[4:] + "/asset.html"
```
Here, *aid* is the *assetid* parameter present in all video links from NBC's website. Usually, it's a 7 digit number, but it could be different. Looking at the code for their javascript player, I found that a "/" must be inserted after every fourth character of *aid* before inserted into *aurl* above. Now, I was lazy and hacked something that will only work for a 7 digit *assetid*. If your favorite sport deviates from this convention, you can try to fix it along these lines.

**URLs expire or never connect:** Yes, I've also noticed that stream URLs do expire, sometimes under a minute. Sorry, no clue what's going on here. I've noticed that some Rewind streams never connect for me. I guess, Microsoft is still winning here. If anyone finds a consistent way to get these to work, please post here.

I hope everyone is enjoying the coverage. Once you get past NBC's website, their video feeds are great!

---

### Post by mooseydoom on 2008-08-14
I find that launching the player in the same command as running the script helps prevent the link from timing out, but there's still no audio for me.  

ex:
vlc $(./nbcsched.py basketball rewind China | grep -A 2 "Game 12" | grep "^mms")

---

### Post by edoviak on 2008-08-15
> **mooseydoom said:**
> I find that launching the player in the same command as running the script helps prevent the link from timing out, but there's still no audio for me.
Thanks for the tip. Launching the player in the same command doesn't resolve the time out troubles for me, but you helped me solve the sound problem.

Sound works with gxine and kaffeine if you have w32codecs installed (and the programs are configured to use them). For example: 

kaffeine $(python ~/.nbcsched.py basketball | grep -A 2 Latvia | grep "^mms")
OR
gxine $(python ~/.nbcsched.py basketball | grep -A 2 Latvia | grep "^mms")


In case it's relevant, I'm running Debian Lenny (not Ubuntu).

---

### Post by Quicksilver_Johny on 2008-08-15
> **mooseydoom said:**
> I find that launching the player in the same command as running the script helps prevent the link from timing out, but there's still no audio for me.  

ex:
vlc $(./nbcsched.py basketball rewind China | grep -A 2 "Game 12" | grep "^mms")

I've been doing something similar, using this script to download videos automatically by importing subprocess and then replacing the printout with:
```
subprocess.Popen('mplayer -dumpstream -dumpfile "'+match+'" "'+asset+'"',shell=True).communicate()
```
I've also been playing the videos with mplayer and w32codecs, having no sound problems at all (except maybe a <4s A/V unsync).

Edit: This does have the problem of mplayer having to restart downloads completely if they don't finish. Anyone have a solution for continuing mms downloads? I'm not sure this is possible.

---

### Post by tomslick42 on 2008-08-15
Is there anyone out there familiar with Firefox add-ons? I stripped the python script to take just the asset-id and have great luck just copying and pasting the asset ID from the URIs and browsing direct, just like mooseydoom was showing with vlc. If we could just hack into Firefox's context menu, extract the asset-id from the <A> target of some of these videos ...

---

### Post by k_i_k on 2008-08-15
> **Quicksilver_Johny said:**
> Edit: This does have the problem of mplayer having to restart downloads completely if they don't finish. Anyone have a solution for continuing mms downloads? I'm not sure this is possible.

I've been recording all the mms streams using mimms (it's packaged for Debian, probably Ubuntu also). mimms -r is supposed to resume a stream. Have not tried it. Someone should give it a shot, though.

---

### Post by edoviak on 2008-08-15
> **k_i_k said:**
> **URLs expire or never connect:** Yes, I've also noticed that stream URLs do expire, sometimes under a minute. Sorry, no clue what's going on here. I've noticed that some Rewind streams never connect for me. I guess, Microsoft is still winning here. If anyone finds a consistent way to get these to work, please post here.

I found the solution to the "dropped streams problem:" Tap into your neighbor's unsecured wireless network. Works great!

Then get on the phone with your internet provider and cancel your service.

---

### Post by tomslick42 on 2008-08-15
If you're willing to do a little copy/paste action with a hacked up version of the python code, you can watch any video on NBC's site. I've been watching Gymnastics with this (since the TV coverage is crap).

1. Browse the site for a video you want to watch
2. Click the link to watch and get the failure screen
3. Copy the ASSET ID portion of the URL on the failure screen (on firefox it's shown on top of the window)
4. Open a shell and run the modified script:
```
./nbcquick {asset-id}
```
5. Copy/Paste or Pipe the returned URI and emjoy

Sorry for the hack job on the script, but my wife has been begging to watch Gymnastics ...

---

### Post by Quicksilver_Johny on 2008-08-15
> **k_i_k said:**
> I've been recording all the mms streams using mimms (it's packaged for Debian, probably Ubuntu also). mimms -r is supposed to resume a stream. Have not tried it. Someone should give it a shot, though.
Apparently that's a new feature. I had to manually install [libmms0]("https://launchpad.net/ubuntu/intrepid/i386/libmms0/0.4-2") and [mimms]("https://launchpad.net/ubuntu/intrepid/i386/mimms/3.2.1-1") from launchpad.

But, it works great. Thank you very much! :)

---

### Post by TCWriter on 2008-08-15
Whaddya know - it does work. The Men's 50 Meter prone is playing out, almost as if by magic.

All that's left is to find a win32codecs and I'll be back in business. Thanks Tomslick 42!

**UPDATE: Finally got win32codecs installed, switched to mplayer (don't know why)... and it's working. It's a teensy bit choppy, but hot damn!**

You guys truly are amazing.

---

### Post by AR_Kozz on 2008-08-15
Apparently a lot of us are getting the xml error, I think 5 people have posted the exact same error output including me...

k_i_k how do we access the page before it is parsed, to make the adjustments you mentioned... we've got to see the whole thing before we can know what it's tripping up on... if I understand right how it works... how can I modify the script to just write the whole thing out for me unparsed

also Tomslick how did you manage to find a gymnastics stream from the site listings, all I see there is stuff they don't show on TV... I'd really like to see the track live

---

### Post by junkbar on 2008-08-15
thanks a lot k_i_k and tomslick42! I especially found tomslick42's [method]("http://ubuntuforums.org/showpost.php?p=5595503&postcount=80") useful for playing things I want to play. I've made a couple more modifications to the script both to solve a problem I was having and to streamline the process.

The problem I was having was that it the script returned the ampersand improperly as its html code, so I've modified the script to fix this.

Also I've modified it to automatically play the video in totem-xine (but you can further modify it to work with mplayer or whatever you prefer).

**EDIT: I've set up a tutorial on how to set everything up in this blog post [here]("http://wvarner.blogspot.com/2008/08/how-to-play-videos-from-nbcolympicscom.html"). Hope this helps!**

---

### Post by mefistofeles666 on 2008-08-15
would some1 be able to tell me why when I use ./nbcsomething.py I get

bash: ./nbcquick-rev2.py: Permission denied


it happens everytime I use ./

---

### Post by edoviak on 2008-08-15
> **mefistofeles666 said:**
> would some1 be able to tell me why when I use ./nbcsomething.py I get

bash: ./nbcquick-rev2.py: Permission denied

I have the same problem, but running 

python nbcquick-rev2.py <asset id>

works.

---

### Post by MaindotC on 2008-08-15
I sincerely doubt you guys didn't consider this, but just in case - can you check the permissions by typing:
```

ls -l <filename>

```

Are you guys familiar with permissions like user ownership & group ownership?

---

### Post by qcpw.alp on 2008-08-15
> **strAlan said:**
> 

Are you guys familiar with permissions like user ownership & group ownership?

funny, though I have proper permissions, it only works for me when I set the program as executable.

---

### Post by mefistofeles666 on 2008-08-15
thanks edoviak....it worked like a charm......

any news on the sound problem? are ppl getting sound playing it with mplayer and win32codecs installed?

---

### Post by TCWriter on 2008-08-15
> **mefistofeles666 said:**
> thanks edoviak....it worked like a charm......

any news on the sound problem? are ppl getting sound playing it with mplayer and win32codecs installed?

I just got the sound working on mplayer by adding the Medibuntu repository to my package manager, then installing the win32codecs. 

Why it works in mplayer and not VLC is beyond me (really; I'm a writer, not a programmer) but I'll take it.

---

### Post by edoviak on 2008-08-15
> **strAlan said:**
> I sincerely doubt you guys didn't consider this, but just in case - can you check the permissions ...
Doh! Forgot all about it!

Thanks.

---

### Post by tomslick42 on 2008-08-15
> **mefistofeles666 said:**
> thanks edoviak....it worked like a charm......

any news on the sound problem? are ppl getting sound playing it with mplayer and win32codecs installed?

I found that I had to install the medibuntu repository codecs and also install the ones from [http://www.mplayerhq.hu/design7/dload.html]("http://www.mplayerhq.hu/design7/dload.html") to get my sound working properly. 

I'm using mplayer as it seems to sync the sound better for me. This double-install seemed a little hacky to me, but I'm a hacky kinda guy.

---

### Post by tomslick42 on 2008-08-15
> **AR_Kozz said:**
> Apparently a lot of us are getting the xml error, I think 5 people have posted the exact same error output including me...

k_i_k how do we access the page before it is parsed, to make the adjustments you mentioned... we've got to see the whole thing before we can know what it's tripping up on... if I understand right how it works... how can I modify the script to just write the whole thing out for me unparsed

also Tomslick how did you manage to find a gymnastics stream from the site listings, all I see there is stuff they don't show on TV... I'd really like to see the track live

I go to the nbcolymics site and go into the specific sport links (listed down the left side) then click on the "VIDEO" section for the particular sport. If you look at the status bar while you hover, you can get the asset-id, but I find it easier to click on the video and let it fail in order to get the text selectable to paste into my shell.

If you take the trouble to log in, you can also get the list of live feeds on the home page. Anything that has an ASSET-ID seems to work great with the groundwork k_i_k laid down.

---

### Post by k_i_k on 2008-08-15
> **AR_Kozz said:**
> Apparently a lot of us are getting the xml error, I think 5 people have posted the exact same error output including me...

k_i_k how do we access the page before it is parsed, to make the adjustments you mentioned... we've got to see the whole thing before we can know what it's tripping up on... if I understand right how it works... how can I modify the script to just write the whole thing out for me unparsed

Look at the line in *__init__()* that reads
```
self.html = fixent(self.html)
```
Before this line executes, *self.html* contains the unparsed text of the webpage. You can dump the contents of *self.html* into a file and look at it with your favorite text editor. Also, if you open the URL that's being fetched (which can either be deduced from the global *nowsched* variable or from the *url* argument to *__init__()*) in mozilla/firefox and view its source.

Once you know what the problem is, you can modify *fixent()* to fix it. Also, the [W3C Validator]("http://validator.w3.org/") may be of help.

---

### Post by dark_harmonics on 2008-08-15
Dont' know if this was mentioned yet (long thread) but try this: [http://wvarner.blogspot.com/2008/08/how-to-play-videos-from-nbcolympicscom.html](http://wvarner.blogspot.com/2008/08/how-to-play-videos-from-nbcolympicscom.html)

This got it working for me. I am thankful to the gentlemen who wrote the blog post and script!

---

### Post by mocha on 2008-08-15
FREAKIN SWEET!  Thanks!!!!

---

### Post by mefistofeles666 on 2008-08-15
is anybody else getting this...when the video is played in in xine, it only shows in a strip that is less than an inch thick and like 4 inches of height. and I can't seem to be able to resize it or change the ration....

also, when playing in xine or mplayer, has anyone found how to fastforward to a specific point? in the video?



also, is there a way to give k_i-K a gold metal? I think he deserves the ubuntu Olympic gold metal in the most important event,sticking it to bill gates and its evil corp. >:)

---

### Post by kb3lms on 2008-08-16
I've tried everything in the posts above but I cannot get audio using mplayer - just video. (This is on amd64 hardy)  I keep seeing

Forced audio codec: mad
Requested audio codec family [wma9dmo] (afm=dmo) not available.
Enable it at compilation.
Requested audio codec family [wmadmo] (afm=dmo) not available.
Enable it at compilation.
Cannot find codec for audio format 0x162.

help! This nbcquick script is just great but I really NEED the audio!

---

### Post by mefistofeles666 on 2008-08-16
kb3..did u already installed the win32codecs? and xine?

---

### Post by k_i_k on 2008-08-16
I'll reiterate one of my previous tips, since this problem keeps coming up.

**I get video but not sound:** If you run a 32bit system, just install the w32codecs package (easy to find information about it). If you run a 64bit system: you're out of luck! UNLESS, you jump through several hoops to install a 32bit version of your favorite media player, together with the w32codecs package. Here's [one possible set of hoops]("http://ubuntuforums.org/showthread.php?t=62685") (YMMV). Another possibility is to google for information about Debian's ia32-libs-tools and ia32-archive packages (also, YMMV).

---

### Post by k_i_k on 2008-08-16
> **Quicksilver_Johny said:**
> Apparently that's a new feature. I had to manually install [libmms0]("https://launchpad.net/ubuntu/intrepid/i386/libmms0/0.4-2") and [mimms]("https://launchpad.net/ubuntu/intrepid/i386/mimms/3.2.1-1") from launchpad.

But, it works great. Thank you very much! :)

Quicksilver_Johny, as I haven't yet had a chance to try this feature, can you briefly explain how this feature can be used or useful?

---

### Post by k_i_k on 2008-08-16
Umm, please [digg]("http://digg.com/linux_unix/Viewing_NBC_s_Olympic_video_coverage_from_Linux").

---

### Post by kamehouse on 2008-08-16
Did anyone get the following error message?
I tried 'python nbcsched.py tennis rewind' and this is what I got:
[INDENT]Traceback (most recent call last):
  File "nbcsched.py", line 108, in <module>
    nowsched = Sched(nowurl)
  File "nbcsched.py", line 106, in __init__
    self.livelinks()
  File "nbcsched.py", line 80, in livelinks
    asxurl = m.groups()[0]
AttributeError: 'NoneType' object has no attribute 'groups'[/INDENT]

Haven't try the live option yet. Also tried with nbcquick-rev2.py and same similar message on groups is displayed.

Thanks!

---

### Post by vampirefo on 2008-08-16
> **kamehouse said:**
> Did anyone get the following error message?
I tried 'python nbcsched.py tennis rewind' and this is what I got:
[INDENT]Traceback (most recent call last):
  File "nbcsched.py", line 108, in <module>
    nowsched = Sched(nowurl)
  File "nbcsched.py", line 106, in __init__
    self.livelinks()
  File "nbcsched.py", line 80, in livelinks
    asxurl = m.groups()[0]
AttributeError: 'NoneType' object has no attribute 'groups'[/INDENT]

Haven't try the live option yet. Also tried with nbcquick-rev2.py and same similar message on groups is displayed.

Thanks!


I have no problems watching any video all the scripts work well for me, I use pclinuxos gnome version.

does this work for you? I did modify nbcquick-rev2.py to use vlc instead of totem.

./nbcquick-rev2.py TE3H-BJ-SD37-081608-155803

All of the script in this thread work for me, but I like nbcquick-rev2.py the best my modified version that is. I get sound, video, haven't missed any events live or rewind.

---

### Post by k_i_k on 2008-08-16
> **kamehouse said:**
> Did anyone get the following error message?
I tried 'python nbcsched.py tennis rewind' and this is what I got:
[INDENT]Traceback (most recent call last):
  File "nbcsched.py", line 108, in <module>
    nowsched = Sched(nowurl)
  File "nbcsched.py", line 106, in __init__
    self.livelinks()
  File "nbcsched.py", line 80, in livelinks
    asxurl = m.groups()[0]
AttributeError: 'NoneType' object has no attribute 'groups'[/INDENT]

Haven't try the live option yet. Also tried with nbcquick-rev2.py and same similar message on groups is displayed.

Thanks!

The script didn't find a URL it was looking for in the fetched *.../asset.html* file. Print out the *asset* variable to figure out why the pattern matching didn't work, then figure out how to find the "high" quality stream URL and fix the script's patter to match it.

---

### Post by tomslick42 on 2008-08-16
I got curious, so I started trying to load the "silverlight" streams - and it seems to actually stream. I would be curious if other folks could do some testing, but this "proprietary" software seems to simply be a normal Win32 ASX stream (with additional data I'm sure).

I modified a section in the search section to:

```
	# Skip to stream URLs for "sl" (silverlight?).
	asset = asset[asset.find('"sl"'):]
	s = re.search(asxre,asset)

	# Prefer to stream URLs for "wmp"
	asset = asset[asset.find('"wmp"'):]
	m = re.search(asxre,asset)

	# if no wmp stream, backtrack to a silverlight stream
	if m is None:
		m = s

```

So far, I've seen good success with this system - I was finally able to watch some of the video's that were bombing out for me.

---

### Post by k_i_k on 2008-08-16
> **tomslick42 said:**
> I got curious, so I started trying to load the "silverlight" streams - and it seems to actually stream. I would be curious if other folks could do some testing, but this "proprietary" software seems to simply be a normal Win32 ASX stream (with additional data I'm sure).

I modified a section in the search section to:

```
	# Skip to stream URLs for "sl" (silverlight?).
	asset = asset[asset.find('"sl"'):]
	s = re.search(asxre,asset)

	# Prefer to stream URLs for "wmp"
	asset = asset[asset.find('"wmp"'):]
	m = re.search(asxre,asset)

	# if no wmp stream, backtrack to a silverlight stream
	if m is None:
		m = s

```

So far, I've seen good success with this system - I was finally able to watch some of the video's that were bombing out for me.

I don't think it's that simple. The problem is that *m* is never *None*. So, your if-statement always fails and you just get the "wmp" URL as before. I tried to get those streams to work in a couple of different ways, but couldn't. But, maybe someone else will have more success.

---

### Post by bpny on 2008-08-16
The reason Vlc has no sound is that ffmpeg does not support Windows Media Audio Professional yet. There is a GSoC project here [http://code.google.com/soc/2008/ffmpeg/appinfo.html?csaid=124750E3DFF1EA23]("http://code.google.com/soc/2008/ffmpeg/appinfo.html?csaid=124750E3DFF1EA23")

---

### Post by phrostbyte on 2008-08-16
Wow! The Olympics work for me now. :popcorn:

---

### Post by phrostbyte on 2008-08-16
**How to get get Olympics working on Ubuntu fast:**

First download this script from junkbar:[URL="http://ubuntuforums.org/showpost.php?p=5596248&postcount=84"]
http://ubuntuforums.org/showpost.php?p=5596248&postcount=84[/URL]

Then open a terminal and change directory to where you downloaded the script, usually "cd Desktop".

Then copy and paste this:
```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list; sudo apt-get update; sudo apt-get --force-yes install medibuntu-keyring; sudo apt-get update; sudo apt-get -y install w32codecs totem-xine python-libxml2 python-lxml python-xml; chmod 755 nbcquick-rev2.py; python nbcquick-rev2.py 0815_hd_gaw_hl_l1664
```

You should see some Olympics action.

---

### Post by k_i_k on 2008-08-17
> **k_i_k said:**
> I don't think it's that simple. The problem is that *m* is never *None*. So, your if-statement always fails and you just get the "wmp" URL as before. I tried to get those streams to work in a couple of different ways, but couldn't. But, maybe someone else will have more success.

**tomslick42** let me know that some of the videos are missing "low" and "high" stream URLs in the "wmp" section its asset.html, but still have them in the "sl" section, which point to valid ASX files. So, his version will work as advertised. However, for other videos, the "sl" URLs point to some amorphous binary blobs. Again, YMMV.

---

### Post by sixerjman on 2008-08-17
Thanks for the script k-i-k.  I use mplayer with libmms0, only thing I have to do sometimes is edit the protocol ('mmsh' - mms over HTML) to take out the 'h' as mplayer doesn't have a plugin for that.  Other than that I got pictures and sound.

---

### Post by vampirefo on 2008-08-17
> **bpny said:**
> The reason Vlc has no sound is that ffmpeg does not support Windows Media Audio Professional yet. There is a GSoC project here [URL="http://code.google.com/soc/2008/ffmpeg/appinfo.html?csaid=124750E3DFF1E
A23"]http://code.google.com/soc/2008/ffmpeg/appinfo.html?csaid=124750E3DFF1EA23[/URL]



I have sound on VLC and video as well works great for me, I suspect it's how your codes are built that may be the problem.

---

### Post by sixerjman on 2008-08-17
Thinking of something like sys('mplayer mmsurl')

---

### Post by sixerjman on 2008-08-17
Ahhhh,  

import os

os.system('mplayer .......')

---

### Post by a94060 on 2008-08-17
thank you very much for this.. i just saw this and am watching table tennis ftmfw!!

---

### Post by sixerjman on 2008-08-17
Trying to get track and field live or rewind working (love the high jump and other jumping/field events), per k-i-k's comments/diagnosis on page 8.  I think certain sports may require more tweaking if they are upcoming prime coverage events, they (NBC) may want people glued to the set.

---

### Post by mefistofeles666 on 2008-08-17
I just came across this old url which has old weightlifting rewinds. I couldn't find them regularly on the website. so hope it helps someone. also, I had to use xine or vlc bc mplayer gave me the technical error message.

[http://www.nbcolympics.com/tv_and_online_listings/zone=PT/day=3/sport=WL/online.html](http://www.nbcolympics.com/tv_and_online_listings/zone=PT/day=3/sport=WL/online.html)

---

### Post by TCWriter on 2008-08-18
So which of you is going to write a Python script that upgrades the inane comments by many of NBC's announcers into credible, useful commentary?

Just asking.

---

### Post by dv_2002us on 2008-08-18
> **tomslick42 said:**
> If you're willing to do a little copy/paste action with a hacked up version of the python code, you can watch any video on NBC's site. I've been watching Gymnastics with this (since the TV coverage is crap).

1. Browse the site for a video you want to watch
2. Click the link to watch and get the failure screen
3. Copy the ASSET ID portion of the URL on the failure screen (on firefox it's shown on top of the window)
4. Open a shell and run the modified script:
```
./nbcquick {asset-id}
```
5. Copy/Paste or Pipe the returned URI and emjoy

Sorry for the hack job on the script, but my wife has been begging to watch Gymnastics ...
I'm using Windows XP, but can't access via IE, especially the 'rewinds' ... so I tried the nbcsched.py script and get the following error. 
"from xml.dom.ext.reader import PyExpat ImportError: No module named ext.reader"

I have installed python 2.5.2 but not sure how install the python-libxml's? Appreciate any help on this.

---

### Post by Ehtetur on 2008-08-18
While not helpful what-so-ever to video problem,
here's my take on the [Beijing Olympics]("http://www.faniq.com/images/blog/china-tibet.JPG").

ack, yeah... i'm one of them :)

---

### Post by MaindotC on 2008-08-19
Ha, friggin' sweet!  Still can't get sound but I'll just run it in VM and use that sound.  Anything to see Brasil lose :)

Update: 2-0 ARG, audio in totem-xine but not in VLC.  I'm sure I just haven't read the entire posts yet.  I'll figure it out.  Thanks again to all and I believe I properly distributed the stars to those deserving :)

---

### Post by k_i_k on 2008-08-19
> **dv_2002us said:**
> I have installed python 2.5.2 but not sure how install the python-libxml's? Appreciate any help on this.

Installation instructions from lxml's home page:

[http://codespeak.net/lxml/installation.html](http://codespeak.net/lxml/installation.html)

---

### Post by gabbagabba on 2008-08-20
Can someone help a linux noob with this:

```
 python nbcquick-rev2.py 0815_hd_gaw_hl_l1664
Traceback (most recent call last):
  File "nbcquick-rev2.py", line 66, in <module>
    nowsched = Sched()
  File "nbcquick-rev2.py", line 51, in __init__
    asxurl = m.groups()[0]
AttributeError: 'NoneType' object has no attribute 'groups'

```

Please note that I get the same error for every assetid I've tried. Also, I am outside the U.S. (Canada)

---

### Post by k_i_k on 2008-08-20
> **gabbagabba said:**
> Also, I am outside the U.S. (Canada)

NBC's videos are only accessible from IP addresses within the US.

---

### Post by chaos51 on 2008-08-21
I get the following error and I am in the US.
> ./nbcquick-rev2.py assetid=0818_hd_ttb_en129
Traceback (most recent call last):
  File "./nbcquick-rev2.py", line 66, in <module>
    nowsched = Sched()
  File "./nbcquick-rev2.py", line 51, in __init__
    asxurl = m.groups()[0]
AttributeError: 'NoneType' object has no attribute 'groups'

Any ideas?  I'm on Ubuntu 8.04.1
thanks

---

### Post by chaos51 on 2008-08-21
Sorry, never mind.  I just needed to take out the assetid= from my argument to the script.  

Thanks all for putting this together.

---

### Post by Snoreis on 2008-08-22
So I've been getting this error why I try to run the python program


> 
mpuisis@mpuisis-laptop:~/Desktop$ ./nbcquick-rev2.py 0812_sd_bkm_to_l0228
Traceback (most recent call last):
  File "./nbcquick-rev2.py", line 66, in <module>
    nowsched = Sched()
  File "./nbcquick-rev2.py", line 51, in __init__
    asxurl = m.groups()[0]
AttributeError: 'NoneType' object has no attribute 'groups'
mpuisis@mpuisis-laptop:~/Desktop$ 





Any ideas?

Thanks,

---

### Post by gabbagabba on 2008-08-22
> **Snoreis said:**
> So I've been getting this error why I try to run the python program




Any ideas?

Thanks,

That's the same error I'm getting. I think it's because I am outside the US. Are you as well?

---

### Post by quarkimedes on 2008-08-22
There is a package in the medibuntu repo called w64codecs. which is supposed to be the 64 bit version of the w32codecs package.  I was wondering if anyone had any luck getting sound with it.  Or has anyone been able to get sound on a 64bit system?

---

### Post by tomslick42 on 2008-08-22
> **Snoreis said:**
> So I've been getting this error why I try to run the python program




Any ideas?

Thanks,


These errors indicate that the script cannot find a video stream for that Asset ID. There are two reasons for this. Some of the videos are only available with the MS Silverlight stream, and that's a little hit-and-miss. You can try this script:

[http://ubuntuforums.org/showpost.php?p=5602945&postcount=106](http://ubuntuforums.org/showpost.php?p=5602945&postcount=106)


The other possibility is that you are outside the US (IP address wise). NBC *ONLY* allows US IP addresses in to view the videos. If you get this, you can try the CBC (Canadian) site:

[http://www.cbc.ca/olympics/](http://www.cbc.ca/olympics/)


... or the YouTube site ...

[http://startupmeme.com/youtube-to-show-exclusive-beijing-olympics-2008-coverage/](http://startupmeme.com/youtube-to-show-exclusive-beijing-olympics-2008-coverage/)


Hope this helps.

---

### Post by inagaddadavida on 2008-08-23
Awesome, just got my Ubuntu up and running yesterday, and am watching olympic videos tonight!

---

### Post by TCWriter on 2008-08-26
Thought I'd wrap up this thread with a cheerful thought; NBC took a hit directly in their pocketbook for their decision to use the proprietary MS Silverlight plug-in. 

From Promo magazine:

[INDENT]Before the start of the Beijing Olympics, it was widely reported that NBC Universal intended its coverage of the games as an experiment in how audiences wanted to access video coverage: on TV, on the Web or even via mobile handset. But decisions made by NBC Universal about video format and access kept online viewership at [www.NBCOlympics.com—and](www.NBCOlympics.com—and) online video ad revenues—artificially low, according to an analysis by marketing research firm eMarketer.

...

While the NBCOlympics.com site saw strong traffic, relatively few of those visitors opted to watch video on the site. That was due in large part to a decision to use the Silverlight media player from Microsoft rather than the much more prevalent Adobe Flash player.[/INDENT]

Thanks again to everyone who contributed!

Tom Chandler

---

### Post by sixerjman on 2008-08-28
Thank you TC!, and thanks k-i-k for getting things going.  Nice community effort and I learned more about python in the doing!

---

### Post by varunreeves on 2009-02-27
hello and good recommendation.I tried the -r and it worked for wmv file

---

### Post by hissyfut on 2010-02-13
a little late, just wanted to say thanks the ones who created the great scripts back then.

---

### Post by TCWriter on 2010-02-14
Seems like little has changed the past two years; here it's the Olympics again, and NBC/Microsoft seemingly have made it impossible to watch on Linux.

It seems the Moonlight 2.0 player isn't enough - and the "alpha" version of Moonlight v 3.0 crashes instantly.

Once again, thanks to NBC and MS - enjoy your low ratings...

---

### Post by no2498 on 2010-02-15
ive seen a few on this site
it did cut me short on the daytona race an no truck race

[http://www.channelsurfing.net/](http://www.channelsurfing.net/)

---

### Post by Yellow Pasque on 2010-02-15
Maybe by 2012, we'll have the luxury of HTML5 Olympic videos... or maybe we'll need silverlight 5 (and only have a dysfunctional Linux equivalent) .. or maybe the world will end before it's ever easy to watch Olymic vids on Linux. My money's on the last one.

---

### Post by Benic on 2010-02-20
Installing the [_Moonlight 3.0 alpha version_]("http://www.go-mono.com/moonlight/prerelease.aspx") makes it possible to watch the Olympics, at least on Canadian media (CTV-TSN-RDS-V). The only drawback so far is the impossibility to use the buttons in the screen: you can't use the fullscreen mode, which is pretty bad...

---

### Post by Hyperion_1984 on 2010-02-23
> **Benic said:**
> Installing the [_Moonlight 3.0 alpha version_]("http://www.go-mono.com/moonlight/prerelease.aspx") makes it possible to watch the Olympics, at least on Canadian media (CTV-TSN-RDS-V). 

Which browser are you using? I'm not able to see videos. I only get the consortium logo using Firefox 3.5 and Moonlight 3.0 alpha.

---

### Post by Benic on 2010-02-23
I use Firefox 3.5. Moonlight 3.0 isn't always working, sometimes you get stuck with the logo. You have to restart Firefox and try again. As far as I know, refreshing the page or going back/forth don't work. If you can see something, don't touch anything!

---

