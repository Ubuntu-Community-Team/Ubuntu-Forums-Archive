---
title: "Firefox 4/Beta"
date: 2010-11-20
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by kaldor on 2010-11-20
Will Firefox 4 or Firefox 4 Beta make its way into 11.04? 

Curious is all.

---

### Post by kaldor on 2010-11-20
New update answered thsi for me. Seems Beta 7 is up.

---

### Post by Anduu on 2010-11-20
I got the update yesterday.

Firefox 4 is supposed to arrive early 2011 and Natty in march so I imagine Firefox 4 should be final by then.

---

### Post by davideotape on 2010-11-21
Got the update, but it's not working :( It's okay though, cause I've been using the beta from Mozilla for a couple of months now, and that's still working fine :)

---

### Post by JRV on 2010-11-21
> **kaldor said:**
> Will Firefox 4 or Firefox 4 Beta make its way into 11.04? 

Curious is all.

Yes, it's in the daily build.

---

### Post by MacUntu on 2010-11-21
Hm, no mouse gestures. I really love Opera.

---

### Post by Merk42 on 2010-11-21
> **MacUntu said:**
> Hm, no mouse gestures. I really love Opera.While not included by default, there are a number of extensions for Firefox that provide mouse gestures

---

### Post by MacUntu on 2010-11-21
> **Merk42 said:**
> While not included by default, there are a number of extensions for Firefox that provide mouse gestures

I usually use FireGestures but that doesn't work with the beta. I don't like this kind of modularity... mouse gesture support should be integrated. :?

---

### Post by Merk42 on 2010-11-21
> **MacUntu said:**
> I usually use FireGestures but that doesn't work with the beta. I don't like this kind of modularity... mouse gesture support should be integrated. :?Then you'd get people going "Well I don't use it, therefore it's bloat BLOAT **BLOAT**"

---

### Post by rajeev1204 on 2010-11-23
Why does my version say beta8pre and not beta 7. Iam on meerkat and using the mozilla ppa

---

### Post by chrisccoulson on 2010-11-23
> **rajeev1204 said:**
> Why does my version say beta8pre and not beta 7. Iam on meerkat and using the mozilla ppa

Because you are using the daily build

---

### Post by rajeev1204 on 2010-11-23
Ok so that means b8 is in daily build and not yet ready for public consumption .

Is there any PPA  with public beta ? I have many problems with this b8pre.

---

### Post by arpanaut on 2010-11-23
> Why does my version say beta8pre and not beta 7. Iam on meerkat and using the mozilla ppa

Have you tried FoxTester?  [http://firefox-tutorials.blogspot.com/2010/08/firefox-4-download-install-customize.html](http://firefox-tutorials.blogspot.com/2010/08/firefox-4-download-install-customize.html)

A good way to use/test Fireox 4 on older installs.

---

### Post by Anduu on 2010-11-23
> **rajeev1204 said:**
> Ok so that means b8 is in daily build and not yet ready for public consumption .

Is there any PPA  with public beta ? I have many problems with this b8pre.

I believe the public beta is b7 which is now default in Natty.

Disable the daily ppa and remove/reinstall Firefox.

---

### Post by jppr on 2010-11-23
Oh my <snip> God = ( 
Firefox 4 b7 IS default in Natty. People... update your system!!
[https://launchpad.net/ubuntu/natty/+source/firefox/4.0~b7+nobinonly-0ubuntu3]("https://launchpad.net/ubuntu/natty/+source/firefox/4.0%7Eb7+nobinonly-0ubuntu3")

---

### Post by go7Ul1ai on 2010-11-23
> **jppr said:**
> Oh my <snip> God = ( 
Firefox 4 b7 IS default in Natty. People... update your system!!
[https://launchpad.net/ubuntu/natty/+source/firefox/4.0~b7+nobinonly-0ubuntu3]("https://launchpad.net/ubuntu/natty/+source/firefox/4.0%7Eb7+nobinonly-0ubuntu3")

Dude, it has been default for at least a few days now :P

---

### Post by kaldor on 2010-11-24
Not sure how it'll work in Ubuntu, but on Debian I use this Iceweasel repo:

```
http://mozilla.debian.net/packages/ ./
```

It syncs with the Firefox beta releases. Maybe it's of use to some of you.

---

### Post by zika on 2010-11-24
You might consider turning Feedback off...
Tools>AddOns...

---

### Post by chrisccoulson on 2010-11-24
> **zika said:**
> You might consider turning Feedback off...
Tools>AddOns...

Why? I enabled it for good reason. What's the point in testing a beta if you're not going to actively participate and provide useful feedback

---

### Post by rajeev1204 on 2010-11-25
Any chances of getting the big orange firefox tab like in windows .

I may sound silly but its what attracted me to FF 4.0 in the first place .Signifies change .The other 'behind the hood stuff' will be worked upon anyway.

---

### Post by arpanaut on 2010-11-25
I remember reading somewhere that some major face-lifts to the  menu in the linux version were coming later in development. re:  making it look more like the windows version.  But that was a while back and can't remember where, Maybe in one of those intro-pages "Welcome to Firefox 4"   FAQ   
May not happen in Ubuntu with the Ubuntu Firefox Modifications, and usurping the top left corner with the buttons and all???

---

### Post by woodbj on 2010-11-25
> **rajeev1204 said:**
> Any chances of getting the big orange firefox tab like in windows .

I may sound silly but its what attracted me to FF 4.0 in the first place .Signifies change .The other 'behind the hood stuff' will be worked upon anyway.

It is available in the daily builds I believe

Just add ```
ppa:ubuntu-mozilla-daily/ppa
``` to your sources.

---

### Post by rajeev1204 on 2010-11-25
> **woodbj said:**
> It is available in the daily builds I believe

Just add ```
ppa:ubuntu-mozilla-daily/ppa
``` to your sources.


Yes i got the tab but its not like the windows one .I guess its a theming issue .

---

### Post by rajeev1204 on 2010-11-25
Another question i have for the devs.

Right now if i start private browsing mode, and later close the window, it closes firefox .Why is that ?

Shouldnt both windows be running together ? 

Like i said before, iam using the daily build.

---

### Post by chrisccoulson on 2010-11-25
> **rajeev1204 said:**
> Yes i got the tab but its not like the windows one .I guess its a theming issue .

No, it's not a theming issue. There is no way for Firefox to draw a button in to the titlebar on Linux (because it's rendered by the WM), unless it renders its own decorations ala Chromium.

What we need is client-side decorations in GTK, but there is a lot of resistance to that in the community which means for now that we won't see the nice parts of the Windows version on Linux.

---

### Post by knarf on 2010-11-25
> **chrisccoulson said:**
> No, it's not a theming issue. There is no way for Firefox to draw a button in to the titlebar on Linux (because it's rendered by the WM), unless it renders its own decorations ala Chromium.

What we need is client-side decorations in GTK, but there is a lot of resistance to that in the community which means for now that we won't see the nice parts of the Windows version on Linux.
Alternatively you can use a tiling window manager which obviates the need for window decorations. The tabs will be right there where you want them, without any need for kludgy window decoration overrides.

[IMG]http://www.unternet.org/files/firefox_tabbed_without_window_decorations.png[/IMG]

If you want to have window control buttons you can put those in the top status bar.

This screenshot is made with [Xmonad]("http://xmonad.org/") but the same effect can be had using other tiling window managers.

---

### Post by plun on 2010-12-05
I am using Firefox Sync and it was messed up yesterday after an Mozilla upgrade.

Latest snapshot must be used:
[https://services.mozilla.com/sync/updated/?version=1.5&channel=dev](https://services.mozilla.com/sync/updated/?version=1.5&channel=dev)

I also the needed to change sync-key  (just cancel the script when it stop)

---

### Post by philinux on 2010-12-07
Does anybody miss the bottom status bar?

---

### Post by screaminj3sus on 2010-12-07
> **chrisccoulson said:**
> No, it's not a theming issue. There is no way for Firefox to draw a button in to the titlebar on Linux (because it's rendered by the WM), unless it renders its own decorations ala Chromium.

What we need is client-side decorations in GTK, but there is a lot of resistance to that in the community which means for now that we won't see the nice parts of the Windows version on Linux.

What I Don't understand is why they don't just move the button to the toolbar like chrome then, there's plenty of space and the concept obviously doesn't work on linux as well as it does with aero. And they could also considering adding search keywords like opera and chrome and making the addressbar/searchbar combines to make even more space there.

---

### Post by chrisccoulson on 2010-12-07
> **screaminj3sus said:**
> What I Don't understand is why they don't just move the button to the toolbar like chrome then, there's plenty of space and the concept obviously doesn't work on linux as well as it does with aero. And they could also considering adding search keywords like opera and chrome and making the addressbar/searchbar combines to make even more space there.

Did you try the latest nightlies? There is already a button on the tabbar.

I'm not sure how combining the addressbar and searchbar creates space really, as they're both on the same toolbar already.

---

### Post by chrisccoulson on 2010-12-07
> **philinux said:**
> Does anybody miss the bottom status bar?

No, I'm glad it's gone, it was a complete waste of space. What do you miss about it?

---

### Post by coffeecat on 2010-12-07
> **philinux said:**
> Does anybody miss the bottom status bar?

Yes. When I go to a banking or other https site, where's the padlock icon (or alternative) I can hover over to get the security certificate details? Or whatever replaces it?

---

### Post by screaminj3sus on 2010-12-07
> **coffeecat said:**
> Yes. When I go to a banking or other https site, where's the padlock icon (or alternative) I can hover over to get the security certificate details? Or whatever replaces it?

The colored bar on the left side of the addressbar, click it.

---

### Post by arpanaut on 2010-12-07
> **philinux said:**
> Does anybody miss the bottom status bar?

Heh, I find it a little awkward, but with all the UI changes going on in this release
I'm just going with the flow for now and reserving judgement.

At first I didn't like the changes in Firefox at all, but have been running Minefield for a couple of months now and it seems to be getting better and better.

If you are averse to change, running development this time around, might not be for you! LOL

---

### Post by kaldor on 2010-12-07
At first the lack of a status bar was a "god **** it!" moment, but then I realized it was in the address bar. Much better refinement :)

---

### Post by Starks on 2010-12-07
The status bar was critical for certain addons and the addon bar that replaces that functionaity isn't that visible to end users.

Plus, the addon new bar is needlessly thicker than the status bar ever was.

---

### Post by Finalfantasykid on 2010-12-07
Those extensions will just have to be updated to suit the new UI.  They could be added to the toolbar or could possibly even be a app tab(or whatever they are called).  If it is a popular addon, it probably won't be long before it is compatible with the new UI.

---

### Post by rajeev1204 on 2010-12-08
the links in addressbar are too cluttered and you never know where the address ends and the link begins.

Status bar provided that info very neat.Iam not saying bring back the status bar but the current implementation of the links into the address bar is tough on my eyes at least.I have stopped noticing it completely.

The problem is , everything now seems to be concentrated in one place with the progress bar in the tabs,links in the address bar etc.
Iam tired trying to figure out one from the other.

I hate the addon bar ,its too big and ugly.
An auto hide button for the bar with progress and links would be better but i guess iam not the UI expert.

---

### Post by rajeev1204 on 2010-12-08
> **chrisccoulson said:**
> No, I'm glad it's gone, it was a complete waste of space. What do you miss about it?

You are glad its gone, but the new add-on bar which is twice its size is not a waste of space ?

---

### Post by coffeecat on 2010-12-08
> **screaminj3sus said:**
> The colored bar on the left side of the addressbar, click it.

Thanks. I don't know how I missed that when I was exploring the address bar last night. In fact, when you hover over the coloured bit you get the "Verified by..." message as before.

One little thing that needs attention is that with Firefox 3 if you wanted to organise your bookmarks, you went to Bookmarks > Organise Bookmarks, which is logical. Now it's Bookmarks > Show All Bookmarks. Show all? I think that might throw a few people. It confused me at first.

---

### Post by philinux on 2010-12-08
I'm slowly getting used to the lack of status bar.

But the padlock sign has gone. I have to click the coloured bit in the address bar to see the security details on my internet bank.
Or am I missing something.

---

### Post by screaminj3sus on 2010-12-08
> **chrisccoulson said:**
> Did you try the latest nightlies? There is already a button on the tabbar.

I'm not sure how combining the addressbar and searchbar creates space really, as they're both on the same toolbar already.

It does create a lot of space, as the whole area the google search bar took up is now gone, and all the functionality can be integrated with the addressbar, once these are integrated you know have  a really long addressbar because the search bar isnt there, so there is more then enough space for say a menu button.

And I have used the button in the tab bar, i don't like it it takes a lot of horizontal space from the tab bar. if you could make it a button with no text I would like it, but the current button that says "minefield" takes out a lot of space for tabs.

---

### Post by seeker5528 on 2010-12-08
> **philinux said:**
> Does anybody miss the bottom status bar?

Yeah, the abbreviated link that is shown in the address bar when mousing over a link is often too abbreviated on one or both ends compared to what used to be shown in the status bar at the bottom which often had enough room to display the entire link address.

Later, Seeker

---

### Post by rajeev1204 on 2011-01-15
Beta 9 is out.

[http://www.mozilla.com/en-US/firefox/4.0b9/](http://www.mozilla.com/en-US/firefox/4.0b9/)

---

### Post by dino99 on 2011-01-15
> **rajeev1204 said:**
> Beta 9 is out.

[http://www.mozilla.com/en-US/firefox/4.0b9/](http://www.mozilla.com/en-US/firefox/4.0b9/)

not very new

---

### Post by ronacc on 2011-01-15
> **rajeev1204 said:**
> Beta 9 is out.

[http://www.mozilla.com/en-US/firefox/4.0b9/](http://www.mozilla.com/en-US/firefox/4.0b9/)

that link brings up a page not found , use this one

[http://www.mozilla.com/en-US/firefox/beta/](http://www.mozilla.com/en-US/firefox/beta/)

---

### Post by rajeev1204 on 2011-01-15
> **dino99 said:**
> not very new

Not new? It was released yesterday.

---

### Post by cariboo on 2011-01-15
Firefox was updated to 4.0b9 earlier this week in the repositories. I'll have to check Synaptic history to see exactly when, but it was 3 or 4 days ago.

---

### Post by efflandt on 2011-01-15
If you want a status bar so you can see the full path of links before clicking on them, there is Status-4-Evar [https://addons.mozilla.org/en-US/firefox/addon/status-4-evar/](https://addons.mozilla.org/en-US/firefox/addon/status-4-evar/)

Although, by default that status bar at the bottom seems to be empty, unless you right click it and select Customize to drag whatever you want to it, like Status Text, etc.

What I miss most in Firefox 4 is lack of a way to export/import html bookmarks directly when trying different distros.  I can copy .mozilla/, but then might miss new links from a new system.  Apparently they think sync replaces that, but that is just another password to remember when installing a system, and I do not necessarily want all links from all systems on all systems.

---

### Post by chrisccoulson on 2011-01-15
Beta 9 was tagged in mozilla-central on 10th Jan, and Mozilla normally start their builds shortly after this. We normally upload at this point so that users can test it before it's officially released (sometimes Mozilla respin their builds if testing finds regressions or other blockers, but this didn't happen for b9)

---

### Post by rajeev1204 on 2011-01-15
> **cariboo907 said:**
> Firefox was updated to 4.0b9 earlier this week in the repositories. I'll have to check Synaptic history to see exactly when, but it was 3 or 4 days ago.


Interesting, its true this time looking at this link [https://launchpad.net/ubuntu/+source/firefox](https://launchpad.net/ubuntu/+source/firefox)

But last time i remember beta 8 wasnt updated days after the public release.

---

### Post by efflandt on 2011-01-15
If you want a status bar so you can see the full path of links before clicking on them, there is Status-4-Evar [https://addons.mozilla.org/en-US/firefox/addon/status-4-evar/](https://addons.mozilla.org/en-US/firefox/addon/status-4-evar/)

Although, by default that status bar at the bottom seems to be empty, unless you right click it and select Customize to drag whatever you want to it, like Status Text, etc.

What I miss most in Firefox 4 is lack of a way to export/import html bookmarks directly when trying different distros.  I can copy .mozilla/, but then might miss new links from a new system.  Apparently they think sync replaces that, but that is just another password to remember when installing a system, and I do not necessarily want all links from all systems on all systems.

PS: Thanks coffeecat, didn't even look there.

---

### Post by coffeecat on 2011-01-15
> **efflandt said:**
> What I miss most in Firefox 4 is lack of a way to export/import html bookmarks directly when trying different distros.

It's still there, but badly labelled. In the Bookmarks menu, 'Show All Bookmarks' gives you the same library window that 'Organise Bookmarks' did in Firefox 3. You can import and export html files just as before. I've also enabled the Bookmarks toolbar from View > Toolbars.

---

### Post by aeronutt on 2011-01-15
I'm using Firefox 4.0b10pre. In yahoo mail, I have it set so that all images in emails are blocked by default. When I try to read an email with an image, yahoo puts a button at the top of the email that's supposed to let you see the images for that email ("Show Images").

But in Firefox 4.0, this button doesn't work. It works fine in Chrome and Firefox 3.x.

When I mouse over the button, it hightlights...but when I click on it, nothing happens.


Any ideas?

---

### Post by woodbj on 2011-01-15
> **aeronutt said:**
> I'm using Firefox 4.0b10pre. In yahoo mail, I have it set so that all images in emails are blocked by default. When I try to read an email with an image, yahoo puts a button at the top of the email that's supposed to let you see the images for that email ("Show Images").

But in Firefox 4.0, this button doesn't work. It works fine in Chrome and Firefox 3.x.

When I mouse over the button, it hightlights...but when I click on it, nothing happens.


Any ideas?

I have that same problem. +1 on any ideas

---

### Post by chrisccoulson on 2011-01-16
> **rajeev1204 said:**
> But last time i remember beta 8 wasnt updated days after the public release.

That's because I was on vacation when beta 8 was released. In general, we try to get versions in shortly after they are tagged in Mercurial and when Mozilla start their builds. This means you get the builds a few days before the official release The builds sometimes aren't the final ones if testing finds any serious bugs or regressions, but that didn't happen for the beta 9 release.

---

### Post by rajeev1204 on 2011-01-16
Ah not complaining, just something i had noticed when using Natty.I generally dont like to use PPA's.

I have some questions about hardware accel on firefox, are you the right person to ask? Iam currently using beta10pre from the mozilla daily builds.I have been following the blogs from joegriffin and this here [http://hacks.mozilla.org/2010/09/hardware-acceleration/](http://hacks.mozilla.org/2010/09/hardware-acceleration/)

And also, sometimes the url of a link does not display in the address bar ,is this a known bug?

---

### Post by ssam on 2011-01-19
i recommend that everyone installs the Grafx Bot plug-in to help test the new graphics work in firefox. the wider the range of hardware it is tested on the more bugs will be found, and the more likely stuff can be enabled on linux.

see:
[http://jagriffin.wordpress.com/2010/08/30/introducting-grafx-bot/](http://jagriffin.wordpress.com/2010/08/30/introducting-grafx-bot/)
[https://addons.mozilla.org/en-US/firefox/addon/grafx-bot/](https://addons.mozilla.org/en-US/firefox/addon/grafx-bot/)

if you have tried the past few days the results server is back up now
[http://brasstacks.mozilla.com/resultserv/data/?ffversion=4.0b9&since=7](http://brasstacks.mozilla.com/resultserv/data/?ffversion=4.0b9&since=7)

also if you tried in an older beta then try again to see if the have fixed anything.

---

### Post by tjeremiah on 2011-01-26
does the FEEDBACK extension slow down anyone elses Firefox?

---

### Post by Harry33 on 2011-01-26
There is a new beta10 downloadable in Natty repos now.
Here.
[https://launchpad.net/ubuntu/natty/+source/firefox/4.0~b10+build1+nobinonly-0ubuntu2](https://launchpad.net/ubuntu/natty/+source/firefox/4.0~b10+build1+nobinonly-0ubuntu2)

---

### Post by mvario on 2011-01-28
Is this the place, or can someone point me to the place, where I can inquire about the ubuntu-mozilla-daily release of Firefox 4 i386 Maverick?  I haven't gotten an daily in a week and was wondering.

Newer versions than the last one I received are listed on Launchpad, but they are all tagged "[IMG]https://launchpad.net/@@/build-failed[/IMG]       Failed to build"

And if this PPA is no longer being maintained can anyone suggest a PPA for fairly up to date FF4 Maverick?

Thanks much.

---

### Post by Harry33 on 2011-01-28
> **mvario said:**
> Is this the place, or can someone point me to the place, where I can inquire about the ubuntu-mozilla-daily release of Firefox 4 i386 Maverick?  I haven't gotten an daily in a week and was wondering.

Newer versions than the last one I received are listed on Launchpad, but they are all tagged "[IMG]https://launchpad.net/@@/build-failed[/IMG]       Failed to build"

And if this PPA is no longer being maintained can anyone suggest a PPA for fairly up to date FF4 Maverick?

Thanks much.

Here is one daily a week PPA for Maverick:
[https://launchpad.net/~silverwave/+archive/testing2](https://launchpad.net/~silverwave/+archive/testing2)

But really Ubuntu Mozilla Daily PPA is maintained continuously.
It is just that the FF4 build has failed for all series from Hardy to Natty.
Try later again.

---

### Post by chrisccoulson on 2011-01-28
The issue is that I'm playing catch up this week after spending all my time on globalmenu-extension.

They will be fixed for tonights build ;)

---

### Post by mvario on 2011-01-28
> **Harry33 said:**
> Here is one daily a week PPA for Maverick:
[https://launchpad.net/~silverwave/+archive/testing2]("https://launchpad.net/%7Esilverwave/+archive/testing2")

But really Ubuntu Mozilla Daily PPA is maintained continuously.
It is just that the FF4 build has failed for all series from Hardy to Natty.
Try later again.

Okay thanks, I'll try and wait it out.  I usually have more patience, but it's been a week and the last build I got was kind of wonky, as dailies go.

---

### Post by tghe-retford on 2011-01-28
> **mvario said:**
> ...but it's been a week and the last build I got was kind of wonky, as dailies go.
The last build from the Mozilla Daily Build Team (20110120) has window update problems, and it's been over a week - the amd64 and i386 Firefox 4 sources have failed to build every single day since, I have had to transition to the Firefox 4.0 Beta 10 in the repositories for the time being.

---

### Post by plun on 2011-01-29
> **chrisccoulson said:**
> The issue is that I'm playing catch up this week after spending all my time on globalmenu-extension.

They will be fixed for tonights build ;)

Thank You Chris !!

Latest Minefield up and running...

EDIT  Latest version is really unstable... vBulletin logout is broken and also other issues with vBulletin....  OK with Nattys version.

---

### Post by rajeev1204 on 2011-01-30
Those who are on the daily PPA, you will notice a pleasant surprise ,something is back as a feature.;)




1.One problem i have with this beta and previous ones is sluggish closing of tabs and tab candy.
2.URL's are missing sometimes from addressbar.

---

### Post by mvario on 2011-01-30
Thanks! I've got updates again.  

Anyone know if there will be updates to xulrunner 2 coming also?

Thanks again!!
-Mike

---

### Post by aeronutt on 2011-02-05
> **aeronutt said:**
> I'm using Firefox 4.0b10pre. In yahoo mail, I have it set so that all images in emails are blocked by default. When I try to read an email with an image, yahoo puts a button at the top of the email that's supposed to let you see the images for that email ("Show Images").

But in Firefox 4.0, this button doesn't work. It works fine in Chrome and Firefox 3.x.

When I mouse over the button, it hightlights...but when I click on it, nothing happens.


Any ideas?

Seems a recent update fixed this problem. Now at 4.0b12pre and the 'show images' button works! Yeehaa!

---

### Post by rajeev1204 on 2011-02-10
The url links have moved to the bottom of the page now similar to chrome.So now both page loading status and url links are previewed at the bottom.
Slight difference though is, on moving the mouse over the preview it moves over to the right side ,probably to get out of the way.

I suggest just hiding the status instead of just moving it over to the other side.

---

### Post by jerrylamos on 2011-03-24
> **coffeecat said:**
> It's still there, but badly labelled. In the Bookmarks menu, 'Show All Bookmarks' gives you the same library window that 'Organise Bookmarks' did in Firefox 3. You can import and export html files just as before. I've also enabled the Bookmarks toolbar from View > Toolbars.
Just installed 24 March current daily build.  Under "Help" it just says Firefox 4.0 and nothing about Beta.
I can't find import/export bookmarks.
Select Bookmarks > Show All Bookmarks and there is nothing there to import bookmarks. I've tried right click left click on everything there and there's no way to import bookmarks.

Any clue?

Thanks, Jerry

---

### Post by alphacrucis2 on 2011-03-25
> **jerrylamos said:**
> Just installed 24 March current daily build.  Under "Help" it just says Firefox 4.0 and nothing about Beta.
I can't find import/export bookmarks.
Select Bookmarks > Show All Bookmarks and there is nothing there to import bookmarks. I've tried right click left click on everything there and there's no way to import bookmarks.

Any clue?

Thanks, Jerry

Weirdly it is under Bookmarks - Show All bookmarks.

That displays another screen titled "Library" that has an import and backup button

---

### Post by Harry33 on 2011-03-25
> **jerrylamos said:**
> Just installed 24 March current daily build.  Under "Help" it just says Firefox 4.0 and nothing about Beta.
...


What beta?
Firefox 4 is now rc2.

---

### Post by coffeecat on 2011-03-25
> **Harry33 said:**
> Firefox 4 is now rc2.

I was assuming we now had final, since that has now been released, but you're right. Synaptic tells me that the current version is 4.0~rc2+build3+nobinonly-0ubuntu1. Or did Mozilla simply use the rc2 build for final because it was ready for release? In which case I would see why the Ubuntu devs wouldn't have needed to upgrade FF just to relabel the package as final.

---

### Post by jerrylamos on 2011-03-25
Found import & backup.

Run the cursor over the top line and the choices appear.

Jerry

---

### Post by Harry33 on 2011-03-25
> **coffeecat said:**
> I was assuming we now had final, since that has now been released, but you're right. Synaptic tells me that the current version is 4.0~rc2+build3+nobinonly-0ubuntu1. Or did Mozilla simply use the rc2 build for final because it was ready for release? In which case I would see why the Ubuntu devs wouldn't have needed to upgrade FF just to relabel the package as final.

Right FF 4.0 was released on March 22th.
While FF 4.0~rc2+build3+nobinonly-0ubuntu1 in Natty was uploaded on March 21st:
```
 New upstream release v4.0 RC2 build3 (FIREFOX_4_0rc2_BUILD3).
    D'oh! Should have spotted that before uploading build2
```

---

