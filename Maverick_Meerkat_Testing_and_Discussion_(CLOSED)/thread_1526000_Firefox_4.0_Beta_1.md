---
title: "Firefox 4.0 Beta 1"
date: 2010-07-07
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by plun on 2010-07-07
I am testing Firefox 4.0 directly downloaded from Mozilla and it works just fine. (running directly with the firefox shell-script)

Info:
[http://www.mozilla.com/en-US/firefox/4.0b1/whatsnew/](http://www.mozilla.com/en-US/firefox/4.0b1/whatsnew/)

Downloads:
[http://www.mozilla.com/en-US/firefox/all-beta.html](http://www.mozilla.com/en-US/firefox/all-beta.html)

The tabs can be moved but the GUI is nearly the same....:-k

The ubuntu mozilla daily ppa does not include this version, strange IMHO...

Will Maverick final use Firefox 4.0 ?  Whats the plan ?


[[img]http://ubuntu-pics.de/thumb/97446/snapshot4_kwsdK6.png[/img]](http://ubuntu-pics.de/bild/97446/snapshot4_kwsdK6.png)

---

### Post by chrisccoulson on 2010-07-07
> **plun said:**
> Will Maverick final use Firefox 4.0 ?  Whats the plan ? 

Maverick will almost certainly release with 3.6. The first RC of Firefox 4 is scheduled for October, so it's unlikely that Maverick will ship with it

---

### Post by hikaricore on 2010-07-07
4.0 will probably break half the old addons most of us use.  :p
I'm hesitant to go anywhere near it yet.

---

### Post by Ellipsis on 2010-07-07
Firefox 4 is "supposed to" ship in November... so for about 5 months after release we will have people asking how to install Firefox 4.

---

### Post by ranch hand on 2010-07-07
You can move the tabs in the current version.  At least with desktop effects set at none you can.

---

### Post by plun on 2010-07-07
> **chrisccoulson said:**
> Maverick will almost certainly release with 3.6. The first RC of Firefox 4 is scheduled for October, so it's unlikely that Maverick will ship with it

OK... oh well:tongue:....  "How do we upgrade to Firefox 4.0 ? " :D

Also checked Mozillas wiki:
[https://wiki.mozilla.org/Releases](https://wiki.mozilla.org/Releases)

-----------------------------------

The tabs position is controlled this way in 4.0

[IMG]http://ubuntu-pics.de/bild/97524/snapshot5_e7WFs3.png[/IMG]

I prefer them below navigation toolbar.

---

### Post by Merk42 on 2010-07-07
> **Ellipsis said:**
> Firefox 4 is "supposed to" ship in November... so for about 5 months after release we will have people asking how to install Firefox 4.
Firefox 3 came out AFTER Hardy, Hardy shipped with the beta, and Hardy was an LTS!

So I would HOPE Maverick would ship with Firefox 4 at whatever stage it's at. Otherwise, 5 out of the 6 months before Maverick+1  ABT will be full of "How do I get Firefox 4"

Nope, nothing wrong with Ubuntu's upgrade policy at all.:roll:

And before anyone mentions [this blueprint](https://blueprints.launchpad.net/ubuntu/+spec/desktop-lucid-new-firefox-support-model), I assure you Firefox 4 won't be pushed until 3.6 is EOL which will most likely be far after Maverick+1's release

---

### Post by chrisccoulson on 2010-07-07
> **Merk42 said:**
> And before anyone mentions [this blueprint](https://blueprints.launchpad.net/ubuntu/+spec/desktop-lucid-new-firefox-support-model), I assure you Firefox 4 won't be pushed until 3.6 is EOL which will most likely be far after Maverick+1's release

That's right, we will update stable releases to FF4 when 3.6 approaches EOL. Having been involved with the 3.6 upgrade recently, I can assure you there's a good reason for doing it that way...

---

### Post by Merk42 on 2010-07-07
> **chrisccoulson said:**
> That's right, we will update stable releases to FF4 when 3.6 approaches EOL. Having been involved with the 3.6 upgrade recently, I can assure you there's a good reason for doing it that way...
Such as?

Right now it just seems like procrastinating, or delaying the inevitable. Firefox 4 will have to be ported to Maverick anyway. If 3.X is EOLed 6 months after 4's release, that put it at around May 2011, well within the time that Maverick is supported..

---

### Post by andrewabc on 2010-07-07
Ship with 3.6.x, and as soon (week or two after?) as 4.0 is released send it out as an update.

Problem solved.

Shipping with betas won't be good.

Also, if they can make sure to include 4.0 in repos so if someone wants to easily install it they can.

---

### Post by SoFl W on 2010-07-07
> **plun said:**
> The tabs can be moved but the GUI is nearly the same....

You can move the tabs around in 3.x.  I am sure you could have done it in 2.x.

---

### Post by Merk42 on 2010-07-07
> **andrewabc said:**
> Ship with 3.6.x, and as soon (week or two after?) as 4.0 is released send it out as an update.

Problem solved.As I said, and chrisccoulson confirmed, this won't happen.

> **andrewabc said:**
> Also, if they can make sure to include 4.0 in repos so if someone wants to easily install it they can.Oh there's some completely undiscoverable-you-have-to-ask-to-get-it PPA for recent versions of Firefox.

---

### Post by andrewabc on 2010-07-07
> **Merk42 said:**
> As I said, and chrisccoulson confirmed, this won't happen.

Oh there's some completely undiscoverable-you-have-to-ask-to-get-it PPA for recent versions of Firefox.

Yah, but it would be easy if included in default repository.

Then when someone complains "zomg where's firefox 4!!"
We can just say something like
sudo apt-get install firefox-4.0
etc.

Like how some previous versions were included in older ubuntu releases (but not installed by default).

---

### Post by grandtoubab on 2010-07-08
it seems the question is "when switch to Chromium"
[https://blueprints.launchpad.net/ubuntu/+spec/desktop-maverick-desktop-application-selection](https://blueprints.launchpad.net/ubuntu/+spec/desktop-maverick-desktop-application-selection)

---

### Post by Starks on 2010-07-08
> **chrisccoulson said:**
> That's right, we will update stable releases to FF4 when 3.6 approaches EOL. Having been involved with the 3.6 upgrade recently, I can assure you there's a good reason for doing it that way...
Oh. There's a detail I haven't heard yet.

So, Maverick and other supported releases will never get 4.0 shortly after it comes out, but rather 4.5 (or whatever is out by then) in a year or so when 3.6 actually hits EOL?

---

### Post by hikaricore on 2010-07-08
Nothing is stopping people from updating via alternate sources.

---

### Post by philinux on 2010-07-08
I might give this a whirl.

[http://ubuntuforums.org/showthread.php?t=1452444](http://ubuntuforums.org/showthread.php?t=1452444)

---

### Post by Starks on 2010-07-08
> **hikaricore said:**
> Nothing is stopping people from updating via alternate sources.
True, but the PPA method is far from intuitive.

Your average joe will go to the Mozilla website, download the tarball and go "WTF do I do with this?".

---

### Post by seeker5528 on 2010-07-08
> **Starks said:**
> Your average joe will go to the Mozilla website, download the tarball and go "WTF do I do with this?".

At which point you tell them they should have actually read the instructions instead of just scrolling past them to get to the download link.

But if you are comparing to Windows, there are lots of people who don't know what to do with a .exe file either. ;)

Later, Seeker

---

### Post by Merk42 on 2010-07-08
> **seeker5528 said:**
> But if you are comparing to Windows, there are lots of people who don't know what to do with a .exe file either. ;)

But if we're comparing to Windows they won't need to know what to do with an exe because Firefox would update to 4 automatically.
 ;)

---

### Post by hikaricore on 2010-07-08
> **Merk42 said:**
> But if we're comparing to Windows they won't need to know what to do with an exe because Firefox would update to 4 automatically.
 ;)

Only if you don't have updates disabled, and even then it asks.
Unlike windows itself which updates selectively even when you disable updates.  :p

---

### Post by Sockerdrickan on 2010-07-08
> **andrewabc said:**
> Shipping with betas won't be good.

Also, if they can make sure to include 4.0 in repos so if someone wants to easily install it they can.
+1
Sockerdrickan approves of the message above. sudo apt-get install firefox-4.0

---

### Post by VastOne on 2010-07-08
> **seeker5528 said:**
> At which point you tell them they should have actually read the instructions instead of just scrolling past them to get to the download link.

But if you are comparing to Windows, there are lots of people who don't know what to do with a .exe file either. ;)

Later, Seeker

I have read it til the old eyes bled and missed it...Mind pointing out theses instructions?

And to the topic, I couldn't get any flash to work on Maverick 64 with FF4.0 beta

---

### Post by phillw on 2010-07-08
....>  Stay tuned, because there is more to come and we plan to release new beta versions every two to three weeks.....

There you are, no complaining that the meerkat is okay, go sign up for it :D

[Quote for post](http://blog.mozilla.com/blog/2010/07/06/firefox-4-beta-1-tell-us-what-you-think/)

Although, for those who want cutting edge ...

> Firefox 4 Beta 1 includes dozens of major features and improvements – ....... If you are using a Windows PC, the most noticeable new feature will be the look of the browser. We moved the tabs to the top to make it easier to focus on the web content and easier to control the tools in your Web browser. Also, if you have Windows 7 or Windows Vista the Menu bar was replaced with a single Firefox button so you can get to the most used options with just one click. These changes will be coming soon for Mac and Linux......

Heck it's good to know we linux users get a mention - if you want cutting edge, it seems you need Windows.

ehh, how the world changes.

Regards,

Phill.

---

### Post by ranch hand on 2010-07-08
> **VastOne said:**
> I have read it til the old eyes bled and missed it...Mind pointing out theses instructions?

And to the topic, I couldn't get any flash to work on Maverick 64 with FF4.0 beta

[http://support.mozilla.com/en-US/kb/Installing+Firefox+on+Linux](http://support.mozilla.com/en-US/kb/Installing+Firefox+on+Linux)

---

### Post by piju on 2010-07-08
oh i neeed to try this version of firefox now

---

### Post by Starks on 2010-07-08
You guys are all overreacting.

4.0 is just a relabelled 3.7

Gecko 2.0 = Gecko 1.9.3

---

### Post by VastOne on 2010-07-08
> **ranch hand said:**
> [http://support.mozilla.com/en-US/kb/Installing+Firefox+on+Linux](http://support.mozilla.com/en-US/kb/Installing+Firefox+on+Linux)

Thanks Ranch Hand...

I said that tongue in cheek to point out how it was not on the first page as was suggested (5 layers deep)

And for a push to get the link here...

I should have indicated that...

---

### Post by jppr on 2010-07-09
Is Firefox 4.0 Beta 1 coming in PPA?

---

### Post by hikaricore on 2010-07-09
> **jppr said:**
> Is Firefox 4.0 Beta 1 coming in PPA?

Keep an eye out here: [http://launchpad.net/ubuntu/+ppas?name_filter=Firefox](http://launchpad.net/ubuntu/+ppas?name_filter=Firefox)

It'll probably show up eventually.

---

### Post by ElSlunko on 2010-07-09
Much faster but might be because only 1 of my addons works.

---

### Post by Starks on 2010-07-09
> **jppr said:**
> Is Firefox 4.0 Beta 1 coming in PPA?
Not sure, but                  3.7~a6~hg20100629r46385+nobinonly-0ubuntu1~umd1 from the Ubuntu Mozilla Daily PPA, is easily 98% of the code found in the Linux version of 4.0 Beta 1.

---

### Post by seeker5528 on 2010-07-09
> **VastOne said:**
> I have read it til the old eyes bled and missed it...Mind pointing out theses instructions?

Oops. :redface: I guess since the last time I visited the download page (several months ago) they decided it was better to be slick than informative. 

The old download page included information from [here ](http://support.mozilla.com/en-US/kb/Installing+Firefox+on+Linux) at least the part about installing into your home directory and some of the requirements/troubleshooting stuff, then the link that started the download followed that.

Later, Seeker

---

### Post by VastOne on 2010-07-09
> **seeker5528 said:**
>  I guess since the last time I visited the download page (several months ago) they decided it was better to be slick than informative. 


Later, Seeker


+1  Said true, good form...  

I like informative so much better.

It's pretty said when you have to go outside of the site to search for the link that should be right in front of you...

---

### Post by seeker5528 on 2010-07-09
> **Merk42 said:**
> But if we're comparing to Windows they won't need to know what to do with an exe because Firefox would update to 4 automatically.
 ;)

But to update automatically it would have had to be installed ad some point.

Most often if they didn't install it themselves, it's likely they don't know/care about such things.

Similarly on Linux, if they don't know/care about such things, it's not an issue if there is something older than the newest, shiniest version in the distribution.

If people care enough to go the Mozilla web site, find the download, risk that there may be changes that create issues if you run it, then run the version included in the distribution, they should care enough to find the instructions. 

Later, Seeker

---

### Post by ranch hand on 2010-07-09
> **seeker5528 said:**
> But to update automatically it would have had to be installed ad some point.

Most often if they didn't install it themselves, it's likely they don't know/care about such things.

Similarly on Linux, if they don't know/care about such things, it's not an issue if there is something older than the newest, shiniest version in the distribution.

If people care enough to go the Mozilla web site, find the download, risk that there may be changes that create issues if you run it, then run the version included in the distribution, they should care enough to find the instructions. 

Later, Seeker
Yup, nice link to the help section right there for you.  Easy to find the install stuff from that link.

I did that when I first started and had no clue how to do that stuff.  Instructions were a little easier to find.  It doesn't have the Ubuntu additions and I like that.

---

### Post by Starks on 2010-07-09
Just putting this out there...

You will NEVER have proper font hinting or subpixel rendering of fonts in any Linux Firefox build downloaded from the Mozilla website.

---

### Post by qamelian on 2010-07-09
> **Starks said:**
> Just putting this out there...

You will NEVER have proper font hinting or subpixel rendering of fonts in any Linux Firefox build downloaded from the Mozilla website.
I don't know about that. I'm running 4 beta right now and the fonts look exactly the same as they do in 3.6 on my laptop. That certainly wasn't the case with 3.5 downloaded from the Mozilla site though, when Ubuntu shipped with 3.

---

### Post by Starks on 2010-07-09
Unless things have changed, you should only have proper fonts when Firefox is built against a systemwide cairo rather than an internal one.

My fonts are messed up with the 4.0 binary from Mozilla and I can replicate in a Live USB environment.

---

### Post by qamelian on 2010-07-09
> **Starks said:**
> Unless things have changed, you should only have proper fonts when Firefox is built against a systemwide cairo rather than an internal one.

My fonts are messed up with the 4.0 binary from Mozilla and I can replicate in a Live USB environment.
I know what you mean, but none-the-less, my fonts look the same in FF 4 beta as the due in the stock 3.6. I was quite pleasantly surprised to notice this when I launched 4 for the first time!

---

### Post by ElSlunko on 2010-07-09
My fonts look the same too, but flash doesn't work. Though I haven't really tried to remedy the latter.

---

### Post by qamelian on 2010-07-10
> **ElSlunko said:**
> My fonts look the same too, but flash doesn't work. Though I haven't really tried to remedy the latter.
Flash is sort of working for me. Initially, Flash content works fine but after 4 or 5 minutes it gets very choppy.

---

### Post by chrisccoulson on 2010-07-10
The fonts will be slightly different in the Mozilla builds because the Ubuntu builds contain a patch to the in-tree cairo to make it use the Freetype LCD filtering. Upstream Mozilla builds don't use this, so users will usually notice excess colour fringing on LCD's when using subpixel rendering

---

### Post by ranch hand on 2010-07-10
> **chrisccoulson said:**
> The fonts will be slightly different in the Mozilla builds because the Ubuntu builds contain a patch to the in-tree cairo to make it use the Freetype LCD filtering. Upstream Mozilla builds don't use this, so users will usually notice excess colour fringing on LCD's when using subpixel rendering
I  run shiretoko on my stable release (9.04) and  never have any trouble with the fonts at all.  Really cann't tell the difference in the fonts from the Ubuntu versions. 

It is very slightly faster.

---

### Post by jppr on 2010-07-12
Firefox 4.0 beta in PPA [https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa?field.series_filter=Maverick]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa?field.series_filter=Maverick")

---

### Post by pulpo69 on 2010-07-12
i have this ppa installed, firefox 4.0 not showing up.
maybe because i'm on 64 bit?

---

### Post by jppr on 2010-07-12
> **pulpo69 said:**
> i have this ppa installed, firefox 4.0 not showing up.
maybe because i'm on 64 bit?

It´s not ready yet, there is that firefox 4.0 is currently building...

---

### Post by DougieFresh4U on 2010-07-12
> **pulpo69 said:**
> i have this ppa installed, firefox 4.0 not showing up.
maybe because i'm on 64 bit?

> **jppr said:**
> It´s not ready yet, there is that firefox 4.0 is currently building...

Seems to be there now.

---

### Post by zika on 2010-07-12
[http://ubuntuforums.org/showthread.php?p=9580244#post9580244](http://ubuntuforums.org/showthread.php?p=9580244#post9580244)

---

### Post by plun on 2010-07-12
> **jppr said:**
> Firefox 4.0 beta in PPA [https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa?field.series_filter=Maverick]("https://launchpad.net/%7Eubuntu-mozilla-daily/+archive/ppa?field.series_filter=Maverick")

Thanks !

Firefox 4.0 64 bit (Maverick) running without any trouble.

Adblock Plus also works !.......:D   (The one and only addon I use)

---

### Post by zika on 2010-07-12
> **plun said:**
> Thanks !

Firefox 4.0 64 bit (Maverick) running without any trouble.

Adblock Plus also works !.......:D   (The one and only addon I use)Can You post /usr/bin/firefox-4.0?
As You can see from my post above, there is a glitch with "fi" in the version I'm getting from mozilla-daily-ppa...

---

### Post by plun on 2010-07-12
> **zika said:**
> Can You post /usr/bin/firefox-4.0?
As You can see from my post above, there is a glitch with "fi" in the version I'm getting from mozilla-daily-ppa...

Yup, you are right.....

```
plun@plun-laptop:~$ firefox-4.0
/usr/bin/firefox-4.0: 175: Syntax error: end of file unexpected (expecting "fi")
```

I had one another install in /opt which worked.....the version from the ppa is broken.

---

### Post by zika on 2010-07-12
> **plun said:**
> Yup, you are right.....

```
plun@plun-laptop:~$ firefox-4.0
/usr/bin/firefox-4.0: 175: Syntax error: end of file unexpected (expecting "fi")
```

I had one another install in /opt which worked.....the version from the ppa is broken.

:(

---

### Post by zika on 2010-07-12
Fixed, new version arrived!

---

### Post by Old Marcus on 2010-07-12
No update for me, still got the syntax error. :(

---

### Post by plun on 2010-07-12
> **Old Marcus said:**
> No update for me, still got the syntax error. :(

32 bit is ready and 64 bit builds for the moment, see ppa;)

EDIT, No 64 bit pending...

---

### Post by _oOMOo_ on 2010-07-12
> **Old Marcus said:**
> No update for me, still got the syntax error. :(

Add a line after line 89 with a single 'fi' to /usr/bin/firefox-4.0

---

### Post by cariboo on 2010-07-12
Thanks, that worked for me.

---

### Post by zika on 2010-07-13
It lasted less than a day...
```
Errors were encountered while processing:
 firefox-4.0
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up firefox-4.0 (4.0~b2~hg20100712r47341+nobinonly-0ubuntu1~umd1) ...
update-alternatives: error: alternative path /usr/bin/firefox-4.0 doesn't exist.
dpkg: error processing firefox-4.0 (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 firefox-4.0
```(32-bit, did not test 64-bit yet...)

---

### Post by pulpo69 on 2010-07-13
64 bit working. update this morning.

---

### Post by zika on 2010-07-13
> **pulpo69 said:**
> 64 bit working. update this morning.
On Maverick? 32-bit is missing /usr/bin/firefox-4.0 on Maverick ... I did not update my 64-bit machine since I did not turn it on, due to heat...

---

### Post by plun on 2010-07-13
> **zika said:**
> On Maverick? 32-bit is missing /usr/bin/firefox-4.0 on Maverick ... I did not update my 64-bit machine since I did not turn it on, due to heat...

Well... its seems to be a bloody ppa build mess for the moment..#-o

> Currently  1 package building and  21 packages waiting to build.

64 bit works with the "fi" trick, also got one update....I have no starter but it works fine from the terminal.

---

### Post by SilverWave on 2010-07-13
> **Firefox-4.0 - One Daily A Month #1 - Lucid       **
[SilverWave]("https://launchpad.net/%7Esilverwave")Firefox-4.0 - One Daily A Month #1 - ...              
                                                                                
      **PPA description**
The latest firefox without the update hassle.
 One daily a month from ubuntu-mozilla-daily.
______________________________
 Firefox-4.0 - One Daily A Month #1 - Lucid
One update a month.
Firefox and xulrunner only.
Tested in a virtual machine.
______________________________
 sudo add-apt-repository  ppa:silverwave/one-daily-a-month-1
sudo apt-get update
sudo apt-get install firefox-4.0
______________________________
 Disclaimer: Use at your own risk, no guarantees.
> 
                                                    **Firefox-4.0 - One Daily A Month #3 - Karmic       **
[SilverWave]("https://launchpad.net/%7Esilverwave")Firefox-4.0 - One Daily A Month #3 - ...              
                                                                                
      **PPA description**
   The latest firefox without the update hassle.
 One daily a month from ubuntu-mozilla-daily.
______________________________
 Firefox-4.0 - One Daily A Month #3 - Karmic
One update a month.
Firefox and xulrunner only.
Tested in a virtual machine.
______________________________
 sudo add-apt-repository ppa:silverwave/one-daily-a-month-3
sudo apt-get update
sudo apt-get install firefox-4.0
______________________________
 Disclaimer: Use at your own risk, no guarantees.
All tested and working :-)

Based on:

4.0~b2~hg20100712r47317+nobinonly-0ubuntu1~umd2
2.0~b2~hg20100712r47317+nobinonly-0ubuntu1~umd1                                

Enjoy!

---

### Post by anders_c_ on 2010-07-14
Did some peacekeeper benchmarks:

Firefox(v4.0b1) Scored:
3788 Points

Firefox(v3.6.6) Scored:
2372 Points

Chrome(v6.0.463.0) Scored:
10207 Points

Is the speed increase this small for all of you? I don't have any addons on firefox, it's a fresh download from Mozilla page.

---

### Post by ElSlunko on 2010-07-14
> **anders_c_ said:**
> Did some peacekeeper benchmarks:

Firefox(v4.0b1) Scored:
3788 Points

Firefox(v3.6.6) Scored:
2372 Points

Chrome(v6.0.463.0) Scored:
10207 Points

Is the speed increase this small for all of you? I don't have any addons on firefox, it's a fresh download from Mozilla page.


So I'll enjoy my web browsing 3 times more with chrome! (Kidding).

---

### Post by chrisccoulson on 2010-07-15
The missing /usr/bin/firefox-4.0 symlink issue will be fixed in the next build if that hasn't happened already. The symlinks were being installed in to the wrong package

---

### Post by zika on 2010-07-16
> **chrisccoulson said:**
> The missing /usr/bin/firefox-4.0 symlink issue will be fixed in the next build if that hasn't happened already. The symlinks were being installed in to the wrong packageA package failed to install.  Trying to recover:
Setting up firefox-4.0 (4.0~b2~hg20100715r47651+nobinonly-0ubuntu1~umd1) ...
update-alternatives: error: alternative path /usr/bin/firefox-4.0 doesn't exist.
dpkg: error processing firefox-4.0 (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 firefox-4.0

---

### Post by plun on 2010-07-16
> **chrisccoulson said:**
> The missing /usr/bin/firefox-4.0 symlink issue will be fixed in the next build if that hasn't happened already. The symlinks were being installed in to the wrong package

Ok.....but whats up with the ppa and also other ppas....???

20 packages are waiting and latest was 12 hours ago...!

Nothing on Launchpads status page....;)   open-source quality during summer..;)

[http://identi.ca/launchpadstatus](http://identi.ca/launchpadstatus)

---

### Post by zika on 2010-07-17
> **zika said:**
> A package failed to install.  Trying to recover:
Setting up firefox-4.0 (4.0~b2~hg20100715r47651+nobinonly-0ubuntu1~umd1) ...
update-alternatives: error: alternative path /usr/bin/firefox-4.0 doesn't exist.
dpkg: error processing firefox-4.0 (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 firefox-4.0It is OK, now...

---

### Post by tr4nce on 2010-07-18
> **zika said:**
> It is OK, now...

nope it's not. :(

---

### Post by plun on 2010-07-19
New update and everything seems to work... (64 bit)

- App Tabs OK.

- Program entry OK

- Tabs on top which I dont like, unticked "on top" setting

PPA:
[https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa?field.series_filter=Maverick](https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa?field.series_filter=Maverick)

---

### Post by nebosuke on 2010-07-19
I get core dumps from time to time on 32bit. :(

---

