---
title: "cant watch film"
date: 2013-03-08
forum: Multimedia Software
---

### Post by brutzel on 2013-03-08
Hello:)
I try to watch this film: thoughtmaybe.com/just-do-it/
but it doesnt work. I can see the title with the startbutton, which doesnt work, and the window, where the film should play, is black. Normally i can watch anything, no problem. I allowed the scripts for this site, allowed the cookies for the session, but no, it doesnt work. I installed the mplayer from the softwarecenter (usually  using vlc, allways worked very well) and installed openjdk 7 with the iceteaplugin. a bit of everything i read on the way through the helpsites. plugins are up to date, only the quick time isnt, but it leads me to mac without linux link. 
Normally a shockwaveflash would ask for playing, its up to date, i checked, but here nothing happens, just nothing.
Would be very very glad for help, cause this site has a lot of films i would love to watch!
kindly
brutzel

---

### Post by Cheesemill on 2013-03-08
Works fine here, it's just a standard flash video.

Using Firefox with the flash plugin from the repos.

---

### Post by brutzel on 2013-03-08
thx for helping:)
do you mean another one than the shockwave flash plugin?
I have the adobe flash plugin 2012 - 09 - 15 installed too

---

### Post by brutzel on 2013-03-08
i de- and reinstalled the adobe flash plugin. still the same, i cant watch films on this site. 
i dont understand this. anybody else got an idea, what im doing wrong? now i go to sleep, ill be back tomorrow to see, if anybody has posted something. good night:)

---

### Post by brutzel on 2013-03-09
a friend tells me, that on this site the films start automaticly, now could it be that this is the problem? that somewhere i forbided to start automaticly? but how? i checked everything and cant find anything telling not to start films automaticly. i ve got scriptblocker, but allowed the scripts for the site. allowed it in adblock too, but maybe theres something, i dont know. hmm. still hoping for help.

---

### Post by stinkeye on 2013-03-09
Disable your addon blockers and try again.
Works here in opera and FF.

---

### Post by brutzel on 2013-03-09
did this allready, easy with firefox, but film still didnt work. must be something with adobe flash plugin. reinstalled it again today, tried flash aid as well, nothing helps. youtube no problem. strange. flash aid says, that my architecture is 64bit and would suggest another beta plugin, but it doesnt function cause the hash (md5) is not correct while installing the beta version. im not shure which one to take on the homepage of adobe. so i reinstalled the one in the ubuntu software center with all the extras as well.
I ll work myself through the tutorial, in the forum. first i thought it might be a little too old, but its better than nothing. the thing thats really strange is, that all the other sites work... 
and i havent got a lot of time to do research on the topic, im dislocating and tired in the evening and just wanting to watch a film and fall dead asleep;)

---

### Post by brutzel on 2013-03-10
cant believe it: worked through the tutorial ([http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)), did the special flash comands too, still cant watch films on this site thoughtmaybe.com. also not with addons desabled. youtube works fine. inspected with firebug it tells me server down, but why then everybody else can watch the films there?!? tried before the tutorial several other options, multiple de- and reinstalling flashplugin. now i really dont know what to do else. if anybody could help, this would be great. what could it be?!

---

### Post by SeijiSensei on 2013-03-10
Maybe the source is blocked from you somehow?  Can you ping the thoughtmaybe.com servers at 108.162.196.68 or 108.162.197.68?  If so, try running "telnet 108.162.196.88 80" from the command prompt?  Does the server reply?

---

### Post by brutzel on 2013-03-10
thank you Seiji Sensei for helping:)
adblock plus could be blocking, but its disabled for thoughtmaybe! i disabled every addon there. So:
i pinged for the first time in my life... a long line of this 108.162.196.68 came back, again and again and seconds, dont know really how to say, but looks to me like an answer from the pinged server. then i did this: telnet 108.162.196.88 80
and this was the answer:
Trying 108.162.196.88...
Connected to 108.162.196.88.
Escape character is '^]'.
Connection closed by foreign host.

how and why a foreign host closes the connection? strange... 
just have read  10 pages about connection closed by foreign host and there are 10 different answers... hm. 
hoping for further help...

kindly
brutzel

---

### Post by SeijiSensei on 2013-03-11
If the remote host closes the connection immediately, there is likely some rule on the server that blocks connections from your IP address.  The fact that you can connect initially indicates that you're not being blocked by your ISP or anyone else in between you and the remote server.  I'd send an email to the site manager and ask there.

---

### Post by brutzel on 2013-03-14
i deleted this message.

---

### Post by brutzel on 2013-03-16
Sorry SeijiSensei, i didnt see this answer before, only now when i checked for an answer to my last post now... yes i tried before allready to contact the homepage, but under contact nothing appears. hm. i suppose i have to get social and watch the films with friends, which could make this problem to something useful and interesting... but still im quite puzzled how something like this could happen. i think its really strange.

---

### Post by brutzel on 2013-03-17
i tried via proxy, this should work (if its like SeijiSensei says), but it doesnt. still lookin for solution, so i would be happy to try other suggestions. 
i have to lay a lot, cause im handicapped and cant run to friends, every time i have to kill time. today i would have loved to watch a film there, finished a good book and wasnt ready for a new book allready. hm, and i dont like things not working!

---

### Post by stinkeye on 2013-03-17
Install [**_[COLOR="#B22222"]google-chrome[/COLOR]_**]("www.google.com/chrome/") which has it's own flash plugin 
and try.

---

### Post by brutzel on 2013-03-17
wow, now this is funny! i just logged in again to write, that i have installed chromium browser and i will use this one to watch the films there! and here you are with the same idea! works perfect. but im still curious why firefox doesnt... so ill leave this one unsolved, in case somebody knows a trick for firefox, my favourite browser;)
and thank you stinkeye, a pitty you didnt write this allready last week! im too stupid, that i didnt tried this earlier, thinking over and over on a solution for firefox, not seeing the simple way out...
so i log out now and gonna watch finally this wanted films:)
happy dayz!
brutzel

---

### Post by stinkeye on 2013-03-17
> **brutzel said:**
> wow, now this is funny! i just logged in again to write, that i have installed chromium browser and i will use this one to watch the films there! and here you are with the same idea! works perfect. but im still curious why firefox doesnt... so ill leave this one unsolved, in case somebody knows a trick for firefox, my favourite browser;)
and thank you stinkeye, a pitty you didnt write this allready last week! im too stupid, that i didnt tried this earlier, thinking over and over on a solution for firefox, not seeing the simple way out...
so i log out now and gonna watch finally this wanted films:)
happy dayz!
brutzel
I actually looked at this thread when you started it but people were already answering
and thought someone would mention chrome.
Adobe isn't supporting flash on linux anymore.
Chrome uses it's own Pepper Plugin for flash
The sooner flash dies the better.

---

### Post by psablo on 2013-03-17
> **stinkeye said:**
> 
The sooner flash dies the better.

amen to that

---

