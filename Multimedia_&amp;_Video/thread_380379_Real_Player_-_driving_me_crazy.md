---
title: "Real Player - driving me crazy"
date: 2007-03-09
forum: Multimedia &amp; Video
---

### Post by Langstracht on 2007-03-09
After 2 days of trying, I have now given up getting RP to work either alone or with the BBC's Radio Player.

There are innumerable posts about Linux RP "fixes".

I can not say I have tried them all, but I have tried to try them all, only to find libtotem plug ins not there (so not needing deleting), folders that don't exist (Firefox components for example so I can't paste plug ins into them) and on and on.  And I (even) tried to get RP to run with Konqueror (rather than my Firefox "standard").  To no avail.
 
Surely this can not be rocket science.  Doesn't anyone know the download/install process, the files and directories that need to be created, the things that need to be pasted or deleted? 

Appreciate any contributed wisdom.

---

### Post by ssavelan on 2007-03-10
It should not be hard.

Let's see.. I did have some problems initially... been very sturdy for months, though....

I always come in through the democracynow.org page... good mojo...

[http://www.democracynow.org/streampage.pl]("http://www.democracynow.org/streampage.pl")

then hit the download for unix and linux...
[URL="http://www.real.com/freeplayer/?rppr=democracynow.org"]
http://www.real.com/freeplayer/?rppr=democracynow.org[/URL]

REALPLAYER 10 FOR LINUX IS HERE!...

[http://www.real.com/linux?pcode=rn&opage=freeplayer_partner&src=freeplayer_partner]("http://www.real.com/linux?pcode=rn&opage=freeplayer_partner&src=freeplayer_partner")

Wow, that's funny, the little HOWTO link *is* apparently gone.....

well, luckily I should remember

in terminal navigate to the place with the .bin file and type:

chmod a+x RealPlayer10GOLD.bin
sudo ./RealPlayer10GOLD.bin

using sudo will direct the install to /usr/lib/RealPlayer I believe.....
This is where you can find the binary when the install is done.......

Then, go back to the democracynow.org stream (really, this is good mojo) and select the "open with" option.  Navigate to /usr/lib/R.... or wherever you put it... and select the realplay binary.

If it works, you can select "always open this kind of file with this program" or whatever it says.

Now you are ready to see if the more complicated BBC embedded stuff will work.  Also, try the "launch in stand alone player" button(in bbc).

You will probably have to tweek it a bit to get the sound right.... lower the quality, select buffer the whole clip, etc. 

THIS IS NOT ROCKET SCIENCE.  You shouldn't delve into all of the complicated fixes and patches and god-know-what that's out there.  It is really a straight forward process that should take less than 5 mins.

---

### Post by Langstracht on 2007-03-11
Thanks.

Real Player now works "on its own".  

However BBC Radio Player only opens up Real Player in stand alone state ... i.e.  can listen live but no archives which need Radio Player.

This means a missing plug in perhaps?

---

### Post by ssavelan on 2007-03-13
> **Langstracht said:**
> Thanks.

Real Player now works "on its own".  

However BBC Radio Player only opens up Real Player in stand alone state ... i.e.  can listen live but no archives which need Radio Player.

This means a missing plug in perhaps?

hmm.. I think I know what you mean.  I will look into it.  Can you post a link where you are having said problem?

*I actually helped someone!:guitar: *

---

### Post by sdowney717 on 2007-03-13
[http://www.cfru.ca/archive.php](http://www.cfru.ca/archive.php)

I went here and it loaded mplayer and I hear it.

It was an archived link from that democracynow web site.

---

### Post by josephus on 2007-03-13
I've been having problems with RP on BBC when using Firefox as well.  If you load up FF from the command line and click on BBC video links you'll notice that RP returns some seg fault errors.  I suspect that there is something wrong with the code on BBC website which is causing the error and FF is not catching the error properly.  I've used RP and Opera on the same pages and have had no problem.  

I think there is some additional information on the msg boards on the helix player/realplayer page.

---

### Post by ssavelan on 2007-03-14
> **sdowney717 said:**
> [http://www.cfru.ca/archive.php](http://www.cfru.ca/archive.php)

I went here and it loaded mplayer and I hear it.

It was an archived link from that democracynow web site.

So, are you happy with that?

---

### Post by Langstracht on 2007-03-14
This is a belated response to post number 4.

This link:

[http://www.bbc.co.uk/radio/aod/mainframe.shtml?http://www.bbc.co.uk/radio/aod/index.shtml?button](http://www.bbc.co.uk/radio/aod/mainframe.shtml?http://www.bbc.co.uk/radio/aod/index.shtml?button)

lists all BBC services.

Clicking on all of them opens up a second screen which allows either listening to that service "live" or accessing archives.

I have NO problems with any of the "listen using stand alone Real Player" links.  But I have a problem with EVERY archive link each of which relies on BBC's, so called, Radio Player.

As I understand it, it uses Real Player to "produce the sound".  Hence my guess about the plug in,

I would not be using Real Player at all were it not mandated by the BBC to access their content.

Thanks for your help

---

### Post by ssavelan on 2007-03-14
> **Langstracht said:**
> 

I would not be using Real Player at all were it not mandated by the BBC to access their content.

Thanks for your help

I know what you mean.  But, RealPlayer is actually pretty nice.  It is terrible in winduhs with the "go to realplayer store" link built in to the player.  In linux it is a pretty smooth little player once everything is tweaked.

I'm going to check those links and see if I can access the archives.  I too use the bbc and only need realplayer for democracynow and bbc.

---

### Post by josephus on 2007-03-14
For the BBC you can always choose to use WMV playback instead of realplayer.  I had success using the Totem plugin for Firefox along with xine as the backend (gstreamer doesn't seem to play nice, but maybe you can have better luck with it if you play around with it.)

---

### Post by ssavelan on 2007-03-15
> **Langstracht said:**
> This is a belated response to post number 4.

This link:

[http://www.bbc.co.uk/radio/aod/mainframe.shtml?http://www.bbc.co.uk/radio/aod/index.shtml?button](http://www.bbc.co.uk/radio/aod/mainframe.shtml?http://www.bbc.co.uk/radio/aod/index.shtml?button)

lists all BBC services.

Clicking on all of them opens up a second screen which allows either listening to that service "live" or accessing archives.

Thanks for your help

Well, *I* can't currently tell you anything about this.  Totem is in the way and even when I try to delete all of the cookies from bbc so that i might be able to choose realplayer, totem stays in the way, even though it is a real-audio format.  I have not given it my best try yet; but, no obvious apt-get solution come to mind.  Totem says the "cook" audio codec is missing....  I don't want to remove the totem-mozilla plug, because that plays a lot of media for me.....

any thoughts?

I do think that it is important that everyone can conveniently play all streams from bbc (even if they are a front for the illuminati, lol--- they have some [a lot of] quality stuff)

Will try more later....

:(

---

### Post by jakbritton on 2007-03-15
hey, umm i'm having problems with my real player UNinstall. i installed it and it ran fine, but i liked xmms better and i manually deleted the real player directory, which was pretty stupid i guess.

now in my "open with" window it says "open with real player" under "open wtih mplayer" and "open with xmms" 
this is kind of obsessive but its pissing me off. anyone know how i can remove this from the "open with" list? 

i tried the remove button in the open with window but it wouldn't let me get rid of real player. 

any help is appreciated!

---

### Post by ssavelan on 2007-03-16
> **jakbritton said:**
> hey, umm i'm having problems with my real player UNinstall. i installed it and it ran fine, but i liked xmms better and i manually deleted the real player directory, which was pretty stupid i guess.

now in my "open with" window it says "open with real player" under "open wtih mplayer" and "open with xmms" 
this is kind of obsessive but its pissing me off. anyone know how i can remove this from the "open with" list? 

i tried the remove button in the open with window but it wouldn't let me get rid of real player. 

any help is appreciated!

Thanks for posting.  There are a lot of good tid-bits in there. xmms is a media player?  I was wondering what it was.  The media situation is an ongoing struggle and these are just the types of things that need to get fixed.  I can not currently help; but, I am keeping my eyes peeled for solutions.  I had a mozilla plugin manager of some sort that allowed to match the format with the program in a nice GUI way; except that it was so buggy and mutually conflicting with other solutions that I abandoned it long ago.  These kind of problems make me want to dig it up and try to work with it, whatever *it* was.

---

### Post by ssavelan on 2007-03-16
Ah yes, this chap on another thread has posted it.. and its drawbacks.

"This is not an ideal solution, but try the firefox addon "media player connectivity". This will let you select any media player you have to play embedded media, which will open in a new window. It's a bit clunky, but it works:
[https://addons.mozilla.org/firefox/446/](https://addons.mozilla.org/firefox/446/)
I had the same problem, which in my case was due to the mplayer plugins being broken, and I never managed to fix it."

Yeah, I agree, "media player connectivity" is a bit clunky/buggy/etc. but it is almost the best newb media configuring prog. out there.  Just make sure that.... mmm... the other plugins installed are not conflicting outright.

---

### Post by Bias on 2007-03-17
I had the same problem'

Still do if I boot to :-
Ubuntu, kernel 2.6.15-28-386

Booting to :-
Ubuntu, kernel 2.6.15-26-386
however allows this to work, it also lets the wifi card work!

Ubuntu, kernel 2.6.15-26-386 is what you get after you install from the downloaded iso.

Ubuntu, kernel 2.6.15-28-386 is what you get after some automatic updates have fired off.

I suspect there is something(s) that needs tweeking in Ubuntu, kernel 2.6.15-28-386

However I have no idea who to inform of this, if anyone does know please share :)

Those of you who have been struggling with this please let me know if it works, never know it might be just me.

Nick

---

### Post by bren on 2007-06-16
hi bias

you are not alone 
i am on feisty and have the same problem

(real player works on files and on streams but not with BBC streams.    Note the guy who said you can choose to use .wma from BBC is not quite correct.   Many of the bbc progs are .ram only; only a few are .wma)

bren

---

