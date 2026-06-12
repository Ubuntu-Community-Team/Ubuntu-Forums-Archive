---
title: "Amazon Prime Music Issues"
date: 2017-12-06
forum: Multimedia Software
---

### Post by lsutiger on 2017-12-06
I have Amazon Prime. I like the benefit of being able to stream not only the catalog which I have bought from them, but other music also, as part of the package.
I used to be able to do this without issue for quite some time until maybe a month or so ago.
Today I tested on several machines using different web browsers and it looks like Amazon has made it impossible to stream in Ubuntu.
I have tested Ubuntu, Lubuntu and Xubuntu, all 16.04 editions. I have tried with Chromium and Firefox and the results are exactly the same on all three machines. It flutters through a bunch of tracks without playing anything then posts a message that states "Sorry We are unable to complete your action". I also have a Windows machine here. Works without issue there in both Egde and Firefox.
I see that there are several third party apps available, but I do not like adding third party ppas to my system.
Is anyone else experiencing this? If so, is there a work around?

---

### Post by SeijiSensei on 2017-12-06
Have you tried Google Chrome (not Chromium)?

---

### Post by lsutiger on 2017-12-06
Just finished that. Same result.

---

### Post by coffeecat on 2017-12-06
I don't have Amazon Prime, but I do have a large-ish collection of albums bought from Amazon in my Amazon Music Cloud. They stream and play just fine in Firefox in Ubuntu 17.04.

This is not a "works for me" post. I merely make this observation because I doubt that Amazon "has made it impossible to stream in Ubuntu" as you suggest. Sorry that I don't have anything else to offer, but it could be that the problem lies elsewhere than in Ubuntu, even though you are not seeing the same problem in Windows.

---

### Post by lsutiger on 2017-12-06
Understood. Here is what did happen: For well over a year I was able to stream prime music on both Firefox and Chromium. Something changed around two months ago. I thought it was just a server issue, so I went over to Pandora for a a week or so. Tried again without success for two months now. I can not create a ticket with Amazon because they do not support Linux.
BTW, I just tried it at home(all the others were at work). Same exact issue, same exact behavior.
In the end, something quit working that used to work. And that is why I am reaching out to get help.

---

### Post by Yellow Pasque on 2017-12-07
Did Amazon change from Flash to HTML5 or something?
Have you tried spoofing the user agent?

---

### Post by lsutiger on 2017-12-07
I am pretty sure it is still flash. Reason why is that I have/had a flash blocker add on installed on Firefox that would block the content of the player itself from even loading. Previously, I would disable it in order for it to work in Firefox. Troubleshooting this time , I uninstalled it with the same non result.
I will try spoofing the user againt to see if that makes a difference.

---

### Post by lsutiger on 2017-12-07
Spoofing as Edge had the same result

---

### Post by zeller-michael on 2017-12-07
Hello,

I can confirm the problem to play content form Amazon Prime Music using Ubuntu.

If I click "play" in Amazon Prime Music all the music title of the playlist are running by as they would have a length of 0 seconds each. 
Followed by the Message "[COLOR=#000000][FONT=inherit]Tut uns leid. [/FONT][/COLOR][COLOR=#000000][FONT=&quot]Wir können Ihre Aktion nicht abschließen. Bitte versuchen Sie es später erneut.[/FONT][/COLOR]"[COLOR=#000000][FONT=inherit]
[/FONT][/COLOR]
I'm using Ubuntu 17.10 and tested the issue with Firefox 57 and Chromium 62.

BR

---

### Post by lsutiger on 2017-12-07
Thanks for the info. Looks like something stopped communicating correctly between the tw. At this point, how do we troubleshoot it?

---

### Post by Yellow Pasque on 2017-12-07
Take it up with Amazon. Maybe tell them you're running Android so they don't go down the "We don't support Linux" branch of their script.

---

### Post by lsutiger on 2017-12-07
Wouldn't they just tell me to download the app(which works)?

---

### Post by Yellow Pasque on 2017-12-07
*shrug* Tell them you would like their web player to work for... reasons?

---

### Post by mc4man on 2017-12-08
Have amazon prime, don't use their music so,
set up a playlist, added first song on main page (some christmas song
tried, no good.
Then got latest [flash **npapi** for linux]("https://get.adobe.com/flashplayer/otherversions/"), unpacked, put in ~/.mozilla/plugins in place of the one there.
Tried again, works fine, see screens.
 Note:  I'm using FF56

---

### Post by jee.smith on 2017-12-12
Wow, thank you! I've got the same problems.

---

### Post by jbhtexas on 2017-12-16
Same problems here with Ubuntu 16.04 LTS 64-bit.  A bunch of songs fly by in the play bar, and then a message about needing Adobe Flash pops up.  Happens in both FireFox 57.0.1 and Chrome 63.0.3239.84.  I've tried agent spoofing in Chrome, but to no avail.

---

### Post by lsutiger on 2017-12-20
Update - I now receive a message from Amazon stating to update to the latest version of flash. I did so by enabling Canonical Partners in Software and Updates then
```
sudo apt install adobe-flashplugin
```.
Now working

---

### Post by sccman on 2017-12-20
First we need more information from your computer on why you can't play music.

Let's see if you have any error messages with the browsers themself. Try running Chromium and Firefox through the terminal (Ctrl + Alt + T) and then using Amazon Prime Music. If we're lucky, it might give us an error message about the problem in the terminal.

Copy (Ctrl + Shift + C) and paste (Ctrl + V) the text from the terminal to here when you get the problem with Prime again.

---

### Post by Yellow Pasque on 2017-12-20
> **sccman said:**
> First we need more information from your computer on why you can't play music

You should read the post before yours where the OP said the problem was solved. ;)

---

### Post by Lloydb39 on 2018-01-04
I had the exact same problem with 16.04 and Chrome. It is something that did not exist previously. Update: I solved my own problem simply by disabling my adblocker, Adblocker Plus, on the Amazon prime music site.

---

### Post by fornitsumfornis on 2018-01-20
I couldn't find the plugins folder in under ~/.mozilla/plugins (Firefox Quantum on Linux Mint 18) so I placed libflashplayer.so into /usr/lib/firefox/plugins.  The problem is I had to change its permissions (chmod 755) to get it to work.  I'm posting this not necessarily as a work-around, but more in the hopes that somebody can comment on if changing permissions of that file in a system folder is a major security problem.

---

### Post by Yellow Pasque on 2018-01-20
But you do have a ~/.mozilla folder, correct? If so, you can create the plugins folder there.

> somebody can comment on if changing permissions of that file in a system folder is a major security problem. 

It's not a security issue, but you shouldn't put files not belonging to a package in /usr or you can create future packaging conflicts. That's what what /usr/local is for.

---

### Post by jgonick1969 on 2018-02-20
Make sure flash  plugin is still set to "always active" not "ask".   Tends to get switched back to "ask" after updates.

type "about:addons"  in address bar.  Then Choose "plugins" and  make sure flash is set to "always active"

And Yes,  I know this post was marked as "solved"  but this fixed my problem without have to re-install flash.

---

### Post by mrchriz on 2018-02-28
I was having problems with this in Chrome.
I tried the user agent switching idea with little success - however I then tried this particular add on:
[https://chrome.google.com/webstore/detail/user-agent-switcher/bhchdcejhohfmigjafbampogmaanbfkg](https://chrome.google.com/webstore/detail/user-agent-switcher/bhchdcejhohfmigjafbampogmaanbfkg)

For some reason with this user agent add on it worked where other user agent strings didn't.  (I assume there's a slight difference in the string's but I've not compared them).
The page still looks like it's trying to use Flash - however I believe it's actually using the HTML5 player.
I selected Windows 10 Chrome version 61.

You might need to restart the browser after installing the addon.
Once working it allows you to play albums and doesn't present the this page requires flash message, although the browser still shows the flash blocked icon in the address bar.

---

### Post by akilan27 on 2018-02-28
> **mrchriz said:**
> I was having problems with this in Chrome.
I tried the user agent switching idea with little success - however I then tried this particular add on:
[https://chrome.google.com/webstore/detail/user-agent-switcher/bhchdcejhohfmigjafbampogmaanbfkg](https://chrome.google.com/webstore/detail/user-agent-switcher/bhchdcejhohfmigjafbampogmaanbfkg)

For some reason with this user agent add on it worked where other user agent strings didn't. 

Excellent. This worked without doing anything to flash settings. Amazon is purposely blocking Linux/Ubuntu it seems although browser supports everything.

---

### Post by QIII on 2018-02-28
> **akilan27 said:**
> Excellent. This worked without doing anything to flash settings. Amazon is purposely blocking Linux/Ubuntu it seems although browser supports everything.

That I doubt.  Since they have their own Amazon Linux and Linux has a huge presence on AWS (you can even spin up Ubuntu) and their Amazon EC2, they'd be cutting their own throats.

---

### Post by nikwan3 on 2018-03-07
> **mrchriz said:**
> I was having problems with this in Chrome.
I tried the user agent switching idea with little success - however I then tried this particular add on:
[https://chrome.google.com/webstore/detail/user-agent-switcher/bhchdcejhohfmigjafbampogmaanbfkg](https://chrome.google.com/webstore/detail/user-agent-switcher/bhchdcejhohfmigjafbampogmaanbfkg)

For some reason with this user agent add on it worked where other user agent strings didn't.  (I assume there's a slight difference in the string's but I've not compared them).
The page still looks like it's trying to use Flash - however I believe it's actually using the HTML5 player.
I selected Windows 10 Chrome version 61.

You might need to restart the browser after installing the addon.
Once working it allows you to play albums and doesn't present the this page requires flash message, although the browser still shows the flash blocked icon in the address bar.

This worked! Thanks.. Also, noticing that it has to be changed only once, the first time. Once a song starts, you can reset the user-agent and the next keep playing.

---

### Post by SeijiSensei on 2018-03-07
> **QIII said:**
> That I doubt.  Since they have their own Amazon Linux and Linux has a huge presence on AWS (you can even spin up Ubuntu) and their Amazon EC2, they'd be cutting their own throats.

In general I agree with this, though when it comes to video and audio Amazon has in the past erected roadblocks to machines not running Windows or OS X.  I suspect the pressure for such policies comes from the studios and music publishers who have generally seen Linux users as potentially dangerous pirates.  

[offtopic]Personally, I think such protections are now absurd.  I doubt there is any popular movie, TV show, or album that is not globally available via illegal streaming sites or torrents already.  HBO used to cite piracy figures for "Game of Thrones" almost as a badge of honor.  Most of those viewings came from [illegal streaming sites]("http://variety.com/2017/tv/news/game-of-thrones-piratacy-1202550723/").[/offtopic]

---

### Post by jithinjees on 2018-03-24
> **mrchriz said:**
> I was having problems with this in Chrome.
I tried the user agent switching idea with little success - however I then tried this particular add on:
[https://chrome.google.com/webstore/detail/user-agent-switcher/bhchdcejhohfmigjafbampogmaanbfkg](https://chrome.google.com/webstore/detail/user-agent-switcher/bhchdcejhohfmigjafbampogmaanbfkg)

For some reason with this user agent add on it worked where other user agent strings didn't.  (I assume there's a slight difference in the string's but I've not compared them).
The page still looks like it's trying to use Flash - however I believe it's actually using the HTML5 player.
I selected Windows 10 Chrome version 61.

You might need to restart the browser after installing the addon.
Once working it allows you to play albums and doesn't present the this page requires flash message, although the browser still shows the flash blocked icon in the address bar.

This solution worked for me

---

### Post by redwullf on 2018-04-06
> **jgonick1969 said:**
> Make sure flash  plugin is still set to "always active" not "ask".   Tends to get switched back to "ask" after updates.

type "about:addons"  in address bar.  Then Choose "plugins" and  make sure flash is set to "always active"

And Yes,  I know this post was marked as "solved"  but this fixed my problem without have to re-install flash.

This was the fix for me, thank you!

---

