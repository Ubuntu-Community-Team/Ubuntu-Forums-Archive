---
title: "Can't configue mymote"
date: 2008-12-15
forum: Mythbuntu
---

### Post by bobbob1016 on 2008-12-15
I've been trying to install mymote, a mythtv remote for the iphone/ipod touch, and I can't seem to get it working.  I've done the steps in the manual they have [http://trac2.assembla.com/mymote/wiki/Manual/Requirements](http://trac2.assembla.com/mymote/wiki/Manual/Requirements) but still nothing.  It says loading buttons, and then "could not retrieve key bindings".  When I go into the "info" button at the top right, it says 

"Error while connecting to MySQL database at 'mythbox-ip': (1045) Access denied for user 'mythtv'@'iPod-55.local' (using password: YES)

It does find the mythbox under discovered devices though.  I tried the thing suggested on the 4th post here [http://forums.techguy.org/web-design-development/238985-mysql-access-denied-user.html](http://forums.techguy.org/web-design-development/238985-mysql-access-denied-user.html) and still no luck.  I'd appreciate any help.  Thanks in advance.

Edit: Not sure how, but it is working now.  However, it won't accept button input when I'm watching a movie.  I can navigate there fine, just no input while watching anything.  Any ideas on that?
Edit:Edit: I realized that it is doing the same thing as my original post, just not all the time.  While playing video, it gives me the same issue.
Edit:Edit:Edit: I figured it out, it's a mymote problem.  It only registers .mpg videos as a video, and doesn't change to the video screen unless it's a .mpg.  I figured this out by taking an avi, and copying and changing it to .mpg, the .avi doesn't work with the remote, but the .mpg does.  No transcoding or anything, just a simple rename, so I figure it is a bug.

---

### Post by TrinitronX on 2008-12-24
It seems you got it working.  I also recently had troubles getting it to work, however my problem was due to the password on my mythtv database being something actually more secure than the default "mythtv".

The mymote app really needs to be fixed up to support some actual security instead of promoting the idea that the default password is ok for people to leave that way.  Surprisingly a lot of guides I have seen for mythtv actually tell the user to leave passwords default on purpose!  This is never a good policy, and although it's only for a tv backend device, mischief can still be had upon the database for mythtv.  Who knows, maybe once the database is breached, there are areas of the code that could result in remote code execution.

If I end up having more time on my hands, I think I'm going to go see about messing with mymote's code to make it more configurable, and to have some actual security.

---

### Post by SENDER3 on 2008-12-24
:guitar::guitar::guitar:come on!!Online shop for top quality and lower price for you!

Hello! welcome to our website; http:// [www.shoes-trader.com](www.shoes-trader.com)
our company professional wholesale name brands clothes, shoes, handbags, ect, and every month we all can offer you the newest styles and hot sell items.
We offer have the best services, high quality, fast delivery and reasonable price
My company aim:
1).Quality is the power that our enterprise survive for ever;
2)pace is the magic weapon that we win.
3)Payment method : western union/money gram.
4)Min order :6 mixed piceces order
5)Packing: All the products are packed with original Bags and tags also retro cards/ code numder
6)Shipment: fast and safe delivery. Goods will be received in about 5-7 days.
7)Feature:the best quality, competitive price and the best service
welcome to order now!!
website: http:// [www.shoes-trader.com](www.shoes-trader.com) msn is [email]tradersshoes@hotmail.com[/email]

---

