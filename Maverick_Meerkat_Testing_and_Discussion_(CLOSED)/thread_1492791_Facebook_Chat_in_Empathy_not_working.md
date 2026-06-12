---
title: "Facebook Chat in Empathy not working"
date: 2010-05-25
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by go7Ul1ai on 2010-05-25
I have had this problem for a few days on my Meerkat, Facebook Chat on Empathy won't connect at all, yet MSN connects totally fine. Is anyone else having the same problems? Can someone help me remedy this?

Lee :)

---

### Post by qamelian on 2010-05-25
I have the opposite problem with Empathy. Facebook chat connects flawlessly through their  jabber implementation, but MSN won't connect at all unless I do a killall on telepathy-butterfly, then disable and re-enable MSN in the Accounts dialog.

---

### Post by terry_gardener on 2010-05-25
I have never been able to connect to empathy facebook chat either using the jabber or facebook sections.
also got this fault on lucid

---

### Post by vikrant82 on 2010-05-25
Working here both - msn and facebook

Login: > user@chat.facebook.com

Override server settings: 
chat.facebook.com
5222

Packages:
```
ii  libtelepathy-farsight0                                   0.0.13-1                                                Glue library between telepathy and farsight2
ii  libtelepathy-glib0                                       0.10.1-1ubuntu2                                         Telepathy framework - GLib library
ii  python-telepathy                                         0.15.17-1                                               Python language bindings for telepathy
ii  telepathy-butterfly                                      0.5.10-1                                                MSN connection manager for Telepathy
ii  telepathy-gabble                                         0.9.11-1                                                Jabber/XMPP connection manager
ii  telepathy-haze                                           0.3.4-1                                                 A telepathy connection manager that use libp
ii  telepathy-idle                                           0.1.6-1                                                 IRC connection manager for Telepathy
ii  telepathy-mission-control-5                              5.4.0-1                                                 management daemon for Telepathy real-time co
```

---

### Post by donniezazen on 2010-05-25
> **lee.jarratt said:**
> I have had this problem for a few days on my Meerkat, Facebook Chat on Empathy won't connect at all, yet MSN connects totally fine. Is anyone else having the same problems? Can someone help me remedy this?

Lee :)

Yes Facebook Chat is not working.

---

### Post by terje83 on 2010-05-27
Could this be due to some error in a protocol? I recently upgraded several of the libs tied to empathy in lucid and I have the same problem.

---

### Post by ubuntwinkel on 2010-06-05
I tried what vikrant82 said, and it works for me:
> Login: [email]user@chat.facebook.com[/email]


The Empathy dialog instructions say use only username.  That never worked.

---

### Post by dext on 2010-06-05
Facebook Connection in Empathy has never worked for me where as Pidgin it does work. every other Protocol i use such as MSN/Yahoo etc works, just not facebook

---

### Post by nortoncillo on 2010-06-12
using the 

> user@chat.facebook.com

worked for me

should go like this...
for user john smith who has [http://www.facebook.com/john.smith](http://www.facebook.com/john.smith)
the login should look like 
[email]john.smith@chat.facebook.com[/email]

at first looked as a silly advice, but it's actually working

---

### Post by tito_torrisi on 2010-06-22
It doesn't work since I upgraded to Maverick.
It did before, the jabber AND the facebookchat approach.

It suddenly stopped working. Does someone have a clue why?
It's a fact that it's related to something else, because all the mentioned settings DID indeed work before.

---

### Post by go7Ul1ai on 2010-06-22
Well it's definitely Empathy. Upgrading to the latest version in the PPA in Lucid renders Facebook to not work correctly, I believe it's the same version in Maverick and is still not working. I'll have a look at some bug reports

---

### Post by zodiacdm on 2010-06-22
Yup, same problem here.

Just started a few days ago, my facebook account keeps trying to connect, failing, and giving me a "network error".
Adding @chat.facebook.com did seem to log me in correctly, as it is still trying to log in, the same way my user name does.
changing my user name to the email I log into facebook with stops the connection attempts, so I am guessing the connection is there, just failing at some point...

---

### Post by Luke has no name on 2010-06-23
Facebook chat seems broken, and the icons for online buddies has changed for the worse. Now they are not different colors; and you cannot tell status differences without squinting and hovering over a buddy name.

---

### Post by zodiacdm on 2010-06-23
In the meantime I am just using pidgin for facebook, I use both, as I prefer empathy, but could not get the xfire plugin to work through empathy, and the latest update of the xfire plugin for pidgin is no longer detected by empathy, so I quit trying for now. 

I'm not sure why I prefer empathy exactly, besides the small network icons that appear on each buddy. (I've wanted that out of an IM client for a while..)

Hope to see both of these problems fixed.

---

### Post by go7Ul1ai on 2010-06-24
Fixed as of todays updates for me :) 

I have to say I'm quite happy now ^_^

---

### Post by rodEscobar17 on 2010-07-16
> **nortoncillo said:**
> using the 



worked for me

should go like this...
for user john smith who has [http://www.facebook.com/john.smith](http://www.facebook.com/john.smith)
the login should look like 
[email]john.smith@chat.facebook.com[/email]

at first looked as a silly advice, but it's actually working

This one actually worked for me.

---

### Post by Endomancer on 2010-07-16
For me facebook chat has worked perfectly in empathy until about an hour ago, when in mid conversation I get disconnected. 
Since then facebook authentication keeps failing even though it is the exact same login details that have worked the whole time I been using Lucid.


Then a couple of minutes after posting it starts working again just as mysteriously as it failed

---

### Post by tango_ninja on 2010-07-23
Same here: empathy working fine for msn, gtalk, etc. but facebook won't connect.  Tried [email]user@chat.facebook.com[/email] as well and that didn't work.

---

### Post by kyleabaker on 2010-07-24
> **Luke has no name said:**
> Facebook chat seems broken, and the icons for online buddies has changed for the worse. Now they are not different colors; and you cannot tell status differences without squinting and hovering over a buddy name.

I agree completely about the icons. This design was just not thought out well. I'm also annoyed that I can't easily tell what protocol they are using at a glance without enabling the protocol badge on the status icons. It seems to me that they could find some more elegant and intuitive way to display this information. Surely the status icons will be tweaked before final.

Has anyone seen any official statement about the Facebook plugin? Appending "@chat.facebook.com" to my username fixes the plugin for me and apparently others, but its obviously a bug since this isn't mentioned in the Accounts information for setting up this connection.

I could probably write a patch for this that would use regex to detect whether or not the user specifies this part, and then make changes as necessary, but if its not working for some then I'm curious as to why not.

---

### Post by x-shaney-x on 2010-07-24
I haven't tried facebook chat in empathy since the lucid betas.
Just tried it last night on maverick.  Only entered the username used after the main URL as the account settings say and it all appears to be working fine here.
Didn't need to add @chat.facebook.com or anything else.

---

### Post by nortoncillo on 2010-07-28
now mine is failing... 

...still tries to connect, and seems to get something back, but fails with "network Error" message..

yesterday was working... anyone qith the same problem?

regards

---

### Post by kyleabaker on 2010-07-28
> **nortoncillo said:**
> now mine is failing... 

...still tries to connect, and seems to get something back, but fails with "network Error" message..

yesterday was working... anyone qith the same problem?

regards

The update this morning has broken it again (or so it seems). I was wondering how long it would take for others to bring this back up. Too bad they won't just address this with a permanent fix. :/

---

### Post by kyleabaker on 2010-07-28
Apparently, the issue is with Facebook and not with the Empathy plugin (according to the Digsby blog)..
[http://blog.digsby.com/archives/1476](http://blog.digsby.com/archives/1476)

---

### Post by spesheled1 on 2010-08-08
The "@chat.facebook.com" fix seems to work in Ubuntu Netbook 10.04 with Empathy 2.30.2. Thanks.

---

### Post by doy788 on 2010-08-13
Brilliant work... this advice got me up and running straight away.

Thanks mate!

---

### Post by FrancoNero on 2010-08-14
empathy is such a crappy application... most ubuntuites I know, like myself, install pidgin first thing after setting up the distro...

---

### Post by go7Ul1ai on 2010-08-14
> **FrancoNero said:**
> empathy is such a crappy application... most ubuntuites I know, like myself, install pidgin first thing after setting up the distro...

Well actually, it's just user preference..

---

### Post by dext on 2010-08-14
> **FrancoNero said:**
> **empathy is such a crappy application**... most ubuntuites I know, like myself, install pidgin first thing after setting up the distro... i agree its crap atm, it still is even with the 2.32 branch. i do not know why Pidgin Devs an Empathy Devs just cant work on improving just the 1 Application, the More devs work on 1 App the better it gets,

> **lee.jarratt said:**
> Well actually, it's just user preference.. its gonna be a slow process with Empathy an probbaly slower than it took Pidgin to get to where it is now, butEmpathy is a useless App currently. its a bit like KDE developing another Kopete Messenger when there's already on there to work on an improve,

---

### Post by go7Ul1ai on 2010-08-14
> **dext said:**
> i agree its crap atm, it still is even with the 2.32 branch. i do not know why Pidgin Devs an Empathy Devs just cant work on improving just the 1 Application, the More devs work on 1 App the better it gets,

 its gonna be a slow process with Empathy an probbaly slower than it took Pidgin to get to where it is now, butEmpathy is a useless App currently. its a bit like KDE developing another Kopete Messenger when there's already on there to work on an improve,

Thanks for your opinion, but in my opinion it is not useless.. I use it to chat with friends and it works fine for me :)

---

### Post by sinurge on 2010-08-14
> **lee.jarratt said:**
> Thanks for your opinion, but in my opinion it is not useless.. I use it to chat with friends and it works fine for me :)

Choice, yes it is but i guess most people post installation the 1st thing they would do is install pidgin ... i know i do it. Empathy maybe be good in its own way but in comparison pidgin wins hands down.

I hope empathy develoment speedens up since its inclusion as default in karmic

---

### Post by x-shaney-x on 2010-08-14
Actually I prefer empathy also and on my last mint install one of the first things I did was replace pidgin with empathy.

---

### Post by dext on 2010-08-14
> **lee.jarratt said:**
> Thanks for your opinion, but in my opinion it is not useless.. I use it to chat with friends and it works fine for me :)

Empathy is to slow when it comes to development. however i do like it myself, just that when someone needs something to work an Pidgin does it where Empathy doesnt iv'e had to install Pidgin.

---

### Post by kyleabaker on 2010-08-22
So, am I the only one still having trouble connecting to facebook chat? Or is it still broken for everyone else, too?

---

### Post by ranch hand on 2010-08-22
I can say that I have never had a problem connecting to facebook.

It might be because I have never tried.

---

### Post by jstalnak on 2010-08-30
I'm with Kyle -- well, sorta. I usually use Psi (it's the officially supported client at my office). But after my recent install of Maverick, neither Psi nor Empathy will connect to certain jabber servers (well, the two of them won't connect to one particular jabber server). Pidgin, on the other hand, DOES connect to the jabber server Empathy and Psi will not connect to. How freaking weird is that? Note that Psi, for example, does connect to this same jabber server from home (Lucid 10.04) and from my work Netbook (Lucid 10.04). So, it's got to be something with Maverick. But there's no application error or core. Just a failure to connect.

---

### Post by dext on 2010-08-30
what Empathy Version is in Maverick? if its 2.32 it may depend on GTK3 being installed

---

### Post by jooaakim on 2010-09-16
The solution to this problem seems to be to remove the legacy jabber-facebook protocol that you had in empathy since upgrading from Lucid and adding the account under the proper facebook chat protocol that Empathy in maverick has.

---

### Post by ken_do_san on 2010-09-16
> **nortoncillo said:**
> using the 



worked for me

should go like this...
for user john smith who has [http://www.facebook.com/john.smith](http://www.facebook.com/john.smith)
the login should look like 
[email]john.smith@chat.facebook.com[/email]

at first looked as a silly advice, but it's actually working

Worked for me as well, had been trying for ages to get FB chat to work in Empathy. Thanks guys. :)

---

### Post by Baldrick_NZ on 2010-09-20
> **nortoncillo said:**
> using the 



worked for me

should go like this...
for user john smith who has [http://www.facebook.com/john.smith](http://www.facebook.com/john.smith)
the login should look like 
[email]john.smith@chat.facebook.com[/email]

at first looked as a silly advice, but it's actually working

Which is fine if you actually have a username, cos some don't. All they have is their email addy to connect with which doesn't work under Empathy!

Any ideas how to get around this issue?

---

