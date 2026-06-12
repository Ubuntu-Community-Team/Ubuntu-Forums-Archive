---
title: "Opera can't see internet"
date: 2009-09-03
forum: Networking &amp; Wireless
---

### Post by triplemaya on 2009-09-03
Hi. Just installed Opera, but it can't see the network, I get

 You don't have permission to access / on this server.  etc

Everything else, firefox thunderbird, works fine.

I'm not running a proxy, I've run gnome-network-properties and there's no proxy, the interface is at direct network connection.

Can someone tell me what to try next please :)

---

### Post by wojox on 2009-09-03
```
sudo apt-get --purge remove opera
```

Just joking. Life long Firefox fan.

Check your homepage also.

---

### Post by alienclone on 2009-09-03
im also a FF fan so i dont know Opera, but the 2 things i would check would be..
is it set to work offline?
double check the web address parameters (you know //, not \\ and so forth.

---

### Post by triplemaya on 2009-09-03
Thanks for the replies

I can't find an offline setting, but it's a fresh install, and I'm clicking on the links that came with the install, opera.com, amazon.com, I doubt their spelled wrong!

And I'm a big firefox fan as well, though I'm enjoying swiftweasel even more.
But
Firefox is now 'full up', I have about thirty pages each with several tabs of things I really need to get back to. So starting it up is a big deal! So I use swiftweasel for daily browsing, which is great, and it seems a bit quicker anyway. But of course I get that quite busy, so sometimes it has ten or more pages with multiple tabs. 
So when I just want to put the computer on quick and look up something I want YET ANOTHER browser that isn't stuff up with stuff! that's why I want opera.

Have to say though, I use it on windows - as well as firefox - and I'm getting to like it quite a bit, it is very quick indeed, like instant to start up, touch the icon and it's there.

Most of all I want an extra browser that I like that I can set to the default so when I put the computer on for just one mo to look up something and I click on an html file I don't have to wait for my usual app to start up and look up between ten and a hundred web pages!

I guess tabbed browsing is like fire, great servant, no so terrific master!

---

### Post by r.osmanov on 2009-09-03
Are you sure you have offline mode switched off (File->Work Offline)?
I had some issues with Opera cache. Who knows, maybe cleaning cache will help(Tools->Preferences->Advanced->History->Empty now) ;)

---

### Post by falconindy on 2009-09-03
Also check to make sure there isn't a proxy enabled. Unlikely if its a clean install, but worth checking.

---

### Post by triplemaya on 2009-09-03
Thanks for the reply r.osmanov

No, I've toggled the offline mode, but it's got weirder since then. A lot weirder.

Opera can see the internet, but only one site at a time!?

Last time I turned it on I was getting the internet, but only the me.opera.com subdomain.
google.com, ask.com, downloads.com, even  opera.com, all not accessible. For all other addresses than me.opera.com I got

You don't have permission to access / on this server

!?

But now, when I fire it up, and I have shut down the computer in the meanwhile, it will only get amazon.com home page, and only the text only version, all other addresses not working.
and
All other addresses return the *amazon* 404 not found default page.

but now for the super weird bit
When I tried to go to the me.opera.com subdomain to check on a post I'd made there *with firefox*, I get the *amazon* 404 not found default page.

So I'm a little bit flummoxed, not being a network expert an' all!

And thanks also falconidy, I've checked my ubuntu system with gnome-network-properties and no proxy enabled, and the new install of opera is also suitably without any settings of any kind in that department.

Hopefully there is enough information here that someone who understands these things can decipher it all!

---

### Post by r.osmanov on 2009-09-03
I think it could somehow be caused by connection number settings:
Tools->Preferences->Advanced->Network->Max connections to a server and ...Max total connections.

But, likely, it is better to reset settings to defaults:
Close Opera
```
mkdir /tmp/opera_profile
mv ~/.opera /tmp/opera_profile   # backup settings

```
Launch Opera

---

### Post by triplemaya on 2009-09-04
Many thanks r.osmanov. The code worked perfectly, and I got the first run dialog as it created a new profile when I ran it again.

However, it then tried to connect to 

[http://redir.opera.com/www.opera.com/firstrun/](http://redir.opera.com/www.opera.com/firstrun/)

but nothing, and I then tried all the standard bookmarks again, and the first one I tried, Wikipedia as it happened, worked, but none of the others did.

---

### Post by KeithSloan on 2009-11-13
I have the same problem - so Bump.

I can access my router with 192.168.1.1 and google with 216.239.59.147. i.e. It seems to be something to do with names resolution.

Firefix is working fine

---

