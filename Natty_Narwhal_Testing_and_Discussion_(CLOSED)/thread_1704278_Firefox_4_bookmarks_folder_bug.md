---
title: "Firefox 4 bookmarks folder bug"
date: 2011-03-10
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by coffeecat on 2011-03-10
It's taken me a long time to track down what's causing this, but now I have it.

Open Firefox 4 in Natty Unity and unmaximise it so that it is not covering the whole desktop. Now enable the  Bookmarks Toolbar. If you haven't done so, create one or more bookmarks folders on the toolbar each containing some bookmarks. Don't put bookmarks directly on the toolbar - this bug only manifests with bookmark folders. Now click on one of the bookmark folders. You get a drop-down list of the contained bookmarks? Yes? Good.

Now click on either the Ubuntu logo top-left for the app menu, or the dock Files and Folders launcher, or the dock Applications launcher. Close the black see-through window by clicking anywhere on the empty desktop, not in the firefox window. Now try clicking on one of the bookmarks toolbar folders. You still get a drop-down list? Yes? Good.

Now click on the Ubuntu logo, or Files and Folders launcher, or Applications launcher, but this time close the black window by clicking anywhere in the firefox window. Now click on one of the bookmarks folders. It doesn't open - no drop-down. Yes? That's what I'm getting. The only way to get the bookmarks toolbar to work properly again is to open the applications or Files and Folder window and dismiss it with a click on the desktop, or to open a new Firefox window with ctrl-N.

I don't know whether this is a bug in Firefox or the part of Unity that handles the application/Files and Folders window. Obscure, but curious.

**EDIT**: This only manifests if you close the black window without opening an app or a folder. Clearly then, it only shows if you open an Applications or Files and Folder window and then change your mind.

---

### Post by mc4man on 2011-03-10
Pretty much see the same, at least here the dropdowns can be returned also by just going - focus on desktop, focus back to firefox
Also seems that when dismissing if I click on firefox's window deco (top), it doesn't happen, only when clicking in the body of the firefox window

Edit: it seems the best way to 'dimiss' the dash, places is just to re-click the ubuntu icon

---

### Post by coffeecat on 2011-03-10
> **mc4man said:**
> Pretty much see the same, at least here the dropdowns can be returned also by just going - focus on desktop, focus back to firefox

I hadn't discovered that. That's probably the quickest way to get the drop-downs back. Thanks.

Odd bug, though.

---

### Post by mc4man on 2011-03-10
> 
Odd bug, though.
That it is, can't find anything similar in any other app.
When it goes bad also noticed the r. click context menu on the bookmarks toolbar is unusable, it can be exposed but not used (disappears.
edit: same thing w/ an addon bar in regards to context menu

Found one more oddity w/ this - if in the situation where there is no dropdown then no r. click context works like in trying to copy some text from a web page.

---

### Post by coffeecat on 2011-03-11
Looks like just you and me so far. :) Perhaps no one else is using a bookmarks toolbar.

It happened to me a few more times last night but I'd gone nowhere near the apps or Files and Folder launchers, so I don't know what was triggering it. It was only when I discovered the launchers were causing this that I posted, having something tangible to report.

The good news is that a simple click on the desktop releases the drop downs whatever the cause of them going bad, so thanks for pointing that out.

---

### Post by coffeecat on 2011-03-16
Just thought I'd resuscitate this.

This is still happening a lot, but not necessarily with going anywhere near the dock. Something else must be triggering it, but I haven't worked out what yet. However, a single click on the open desktop restores the bookmarks dropdowns. Also the same right-click menu problem that mc4man mentioned.

Another thing. This doesn't happen with a maximised Firefox.

Must be a Firefox 4 rather than Unity bug. I might try installing FF4 to Windows and/or MacOS to see if the same happens in those OSs.

---

### Post by mbott on 2011-03-27
> **coffeecat said:**
> Looks like just you and me so far. :) Perhaps no one else is using a bookmarks toolbar.

I'd like to use the bookmarks toolbar to import my bookmarks from a back-up file, but the import/restore option is nowhere to be found.  Not that I can find, anyway.  :(

-- 
Mike

---

### Post by coffeecat on 2011-03-27
> **mbott said:**
> I'd like to use the bookmarks toolbar to import my bookmarks from a back-up file, but the import/restore option is nowhere to be found.  Not that I can find, anyway.  :(

Bookmarks menu -> Show All Bookmarks. That gives you the familiar library window, but its menus are in the panel. Make sure you have the library window focussed and you'll find the import and backup menu in the panel. It works the same way as in previous releases but you have global menus and "show all bookmarks" is a confusing way of describing the function of the library window.

---

### Post by mbott on 2011-03-27
Silly me.  As soon as I entered that post, it hit me where to look.  By the time I got back here to correct myself, your reply was posted.

Thanks!  :D

-- 
Mike

---

### Post by rbrick49 on 2011-03-28
I also have a problem with firefox 4 when I open firefox or open bookmark it sometimes gives me a pop up box asking for user name and password the popup box usually has a url address in it.I have tried to take a screenshot but the popup blocks screenshot

---

### Post by coffeecat on 2011-03-28
Is firefox opening with a URL where you have to enter a username and password, such as your router web-interface or a login on a webpage?

Instead of using the Print/Sysreq key for taking a screenshot, you can use the "Take Screenshot" application. It's under  "Accessories" in the "All Applications" drop-down in the dash. With this you can set a delay for taking the grab. Set your delay, click on the "Take Screenshot" button and then see if you can get the username request popup.

---

### Post by rbrick49 on 2011-03-28
here you go coffeecat
this is the best I can do

---

### Post by coffeecat on 2011-03-28
We can't see what's requiring the authentication. You need to set a delay for the grab. Open the take screenshot application and set a delay of 10 seconds. Move the take screenshot window to one side so that it doesn't obscure the authentication window. Open firefox and then click on the 'Take screenshot' button. Wait 10 seconds! :wink:

Alternatively, simply tell us what the words are between "A usernam" and "The site says:", as well as what is on the second line.

---

### Post by rbrick49 on 2011-03-28
here you go mate

---

### Post by coffeecat on 2011-03-28
I'm sorry, I have no idea what localhost:59461 is. I get a "problem loading page" if I try to go to [http://localhost:59461](http://localhost:59461) in Firefox. And besides, you have "about:home" in the address bar with the correct Google page underneath. Apart from erasing all history and all cookies I don't know what to suggest.

Perhaps someone else might be able to help. I couldn't find anything relevant by googling "localhost:59461".

---

### Post by lucazade on 2011-03-28
> **coffeecat said:**
> I'm sorry, I have no idea what localhost:59461 is. I get a "problem loading page" if I try to go to [http://localhost:59461](http://localhost:59461) in Firefox. And besides, you have "about:home" in the address bar with the correct Google page underneath. Apart from erasing all history and all cookies I don't know what to suggest.

Perhaps someone else might be able to help. I couldn't find anything relevant by googling "localhost:59461".

59461 is the number of the TCP port to connect to, usually there is a server behind a port which provide a service

i.e. port 80 - web server
port 21 - ftp server

Dynamic, private or ephemeral ports: 49152–65535

[http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers](http://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_numbers)

---

### Post by coffeecat on 2011-03-28
Ha! Googling the wrong thing. :)

Do you have the Bindwood Firefox extension? (Whatever that is. :?)

[https://answers.launchpad.net/ubuntu/+question/128771](https://answers.launchpad.net/ubuntu/+question/128771)

[http://ubuntuforums.org/showthread.php?t=1633932](http://ubuntuforums.org/showthread.php?t=1633932)

---

### Post by coffeecat on 2011-03-28
> **lucazade said:**
> 59461 is the number of the TCP port to connect to, usually there is a server behind a port which provide a service

Thanks. I notice that the TCP port numbers in the links I've found are different.

---

### Post by lucazade on 2011-03-28
> **coffeecat said:**
> Thanks. I notice that the TCP port numbers in the links I've found are different.

Yep, ports in range 49152&#8211;65535 are usually Dynamic, private or ephemeral ports.
That means are not standardize and probably change everytime, are not static.

Don't know what 59461 is about  sincerly, but that link could give you an idea of ports in general :P

---

### Post by rbrick49 on 2011-03-28
ah hah this problem started after I started loading files to my cloud on ubuntu one thanks folks now do I uninstall firefox or just dowmload a daily build and start from fresh.whens the beta due for release
regards Ron

---

### Post by rbrick49 on 2011-03-28
firefox tools addons bindwood diasable all is ok thanks folks 
regards Ron
buna siera lucozade
excusa my italian spelling please lucozade

---

### Post by lucazade on 2011-03-28
> **rbrick49 said:**
> firefox tools addons bindwood diasable all is ok thanks folks 
regards Ron
buna siera lucozade

;)

---

### Post by lucazade on 2011-03-28
> **coffeecat said:**
> Thanks. I notice that the TCP port numbers in the links I've found are different.

Fyi if you want to know the name of the server behind a port: netstat -anp

---

### Post by deruberhanyok on 2011-04-12
I'm having the same problem as explained in the original post, and, as a solution, click on the desktop seems to clear it.

However, I wanted to post this to say that I'm not actually running Natty (I know this is the Natty testing forum) - I'm running Firefox 4 on Maverick.

My guess is the problem has something to do with Firefox 4 on Linux, then.

My searching skills may be bad but I can't find anything on it in Launchpad - has anyone filed a bug to which I can post details?

[edit] I'm not using bindwood, as others have posted.

---

### Post by iClouseau88 on 2011-04-24
Hi,

I found coffeecat's answer in Post#8 regarding how to locate the bookmark import settings very difficult to understand.  After fumbling around, I chanced upon a way to locate the bookmark import/export settings: I hit the Maximize button in the panel called "Firefox 4" at the top.  From then on, I clicked on Import HTML file to import the bookmarks.html file that was stored in my USB key, select the file and hit Open.

I hope this tip is helpful to some users.

---

