---
title: "How do I send someone a file without email?"
date: 2009-04-11
forum: Networking &amp; Wireless
---

### Post by tomstealthports on 2009-04-11
Okay, first of all, to Joe Sarcasm (in all his many variants)...

I want to send someone a file.  Might be small enough to send via email.  Then again, it may not.  However, I DO NOT WANT TO USE EMAIL.  Nor do I want to make a CD and send it to him via the postal service, private helicopter, donkey, or any other method like that.  I have a computer (linux), he has a computer (also linux), I have a file, I want to send him the file, we both have internet access.

Okay, to everyone else who isn't Joe Sarcasm.  It should be clear that I have little idea what I am doing.  I have heard terms like FTP, SSH, samba and stuff.  However, I have no idea what they are really or how to use them to send someone a file WITHOUT EMAIL.

Can someone give me some starting point?  I mean, it looks obvious to me what I am asking here, I just don't know what would be the best method or approach.  Can someone tell me the simplest way to achieve what I am asking here?

I hope my question is clear.  Sorry if it sounds aggressively worded, if you aren't Joe Sarcasm it isn't directed at you.

If you are Joe Sarcasm, however, STAY THE HELL OUT OF MY THREAD!!!

Thanks to everyone else!

P.S. Here is a diagram of what I'm after:

File on my computer
     |
     |
     |
     V
Sent via Amazing program on my computer to my friend's computer
     |
     |
     |
     V
My friend's computer

---

### Post by ianhaycox on 2009-04-11
The simplest way is most probably a free dropbox (something like dropboks.com) if you aren't too worried about privacy. You copy your file to a server and they copy it from the server to their computer.

Search for free dropbox

ftp, ssh etc need setting up, port fowarding on routers, exposure to the net etc.

---

### Post by tomstealthports on 2009-04-11
Hmm.  I was hoping for something without using third party websites etc. as well.  So from what you're saying, the only way to transfer files from one computer to another without a third computer is with some knowledge of networking and setting complicated stuff up, am I right?

Thanks for the reply, I'm going to edit my post accordingly.

I find it strange that this is so hard.  On windows there are programs that take about two clicks to set up and transfer files from one computer to another.  Like, even I could do it!

-Brainwave?-

Er, could I not just make a torrent and use a torrent program that allows trackerless torrents?  I don't know whether this is possible, or whether such a program exists even, but maybe someone can tell me.

I do realise that I would have to send him the .torrent file somehow first, thanks for pointing that out Joe.

---

### Post by ianhaycox on 2009-04-11
Just out of interest what are the Windows programs that do what you want. Maybe there is an equivalent.

However, unless someone else comes up with another idea, it looks like your friend will need to setup and ftp or ssh server on their pc.

---

### Post by tomstealthports on 2009-04-11
I don't quite remember what the program was called that I used, it was a while ago.  It was freeware and it was similar to smartFTP or cuteFTP except it wasn't those.  I remember it was very very easy to use.  I'll try and find it in a minute.

I think it might have been coreFTP.

What about my bittorrent idea?  Make a torrent with my ip and port as the "tracker", send my friend the .torrent, all done, piece of cake?

No?

How about this...

1. Open transmission

2.  press control+N

3.  click "folder" or "file", navigate to the folder or file you want to send.

4.  Where it says "trackers", click "add"

5.  Enter http://<MY IP ADDRESS>:<MY BITTORRENT PORT>

6.  Click "new", torrent shows up in the same folder as the actual file or folder.

7.  Send torrent to friend via email.

Does that look like a good solution?

---

### Post by Kevbert on 2009-04-11
How about FileZilla FTP. You can read about it [COLOR="Red"][here.]("http://www.linux.com/feature/118843")[/COLOR]

---

### Post by tomstealthports on 2009-04-11
Okay, I'll download filezilla.  Bear in mind, that if my method above works or is capable of working with some modifications, my friend (who is FAR more retarded with computers than I am) only has to double click a .torrent file.

I have to say, after looking at filezilla and its "documentation" pages, my method looks the easiest (if it works or can work)

---

### Post by 3rdalbum on 2009-04-11
Well, what about using something like MSN to do file transfers? The file goes directly peer-to-peer.

Another option: Direct Connect. (never used it actually, but I assume it does exactly what it says on the tin? :-)   )

Another option: Install Apache, open its port on your firewall and forward it to your computer, chuck the file you want to send into /var/www and get your friend to put your IP address in his web browser.

Don't worry - it's easier for you than it sounds; I used to do this years ago when the recipients were really retarded-with-computers. In fact, they were so computer-illiterate that they would sometimes ask me "I just downloaded this file from you, now I can't find it! Where did it go?".

These methods rely on you both having your computers on at the same time. Whenever my friends and I send files and we're not both online at the same time, we use a service like Megaupload.

---

### Post by tomstealthports on 2009-04-11
Hmm.  MSN might be a good option.  I believe it has limits on file size/type, though,  and is pretty slow from what I remember of trying to send files with it.

Direct connect?  Never heard of it.  However, I'd guess that around 0.001% of programs I've tried actually do what I think it says on the tin.  I assume that any files I send via this "direct connect" are routed via a remote robot network in Siberia, passed through China where they make several thousand copies of my file, and finally delivered to Australia, where my friend most certainly is not.  Maybe I'll try it.

Apache sounds easy and simple.  I therefore assume it isn't.  Another one to install, try for five seconds, then uninstall I guess.

So...........no one wants to tell me whether I can do it with bittorrent?  Here is my perspective...

1. I and my friend know how to use bittorrent applications.

2.  My method above looks like it's on the right sort of lines.

3.  I don't know how to use these other apps and I really, really hate linux documentation pages that assume I am Linus Torvalds himself, with a solid knowledge of all command line operations and parameters,  brought up in the 70's with hard-core, wild-haired UNIX geeks for parents. 

4.  Please, please, for the love of all the gods, tell me if this method might work!!!!!!

Oh, and thanks for the suggestions.  I will look into them, despite my sarcasm (hey, it's my thread after all)

---

### Post by ianhaycox on 2009-04-11
Yes, your method might work, and probably will if you have a uPNP capable router. Try it. If it doesn't then come back.

---

### Post by 3rdalbum on 2009-04-11
I'm sorry I don't know enough about Bittorrent to know whether you can have your own computer as the tracker. So I can't comment on the idea.

Using Apache is seriously simple - you don't need to touch any configuration files, just install Apache and it will immediately start serving any files inside /var/www. Put some files in that directory and they will appear to anyone who types your IP address into their web browser. You do need to forward a port (port 80) on your router, but then you'd need to do that anyway if you were running a Bittorrent tracker. Unless you have a direct internet connection, in which case no forwarding necessary.

You can find out your IP address from [www.whatismyip.com](www.whatismyip.com).

---

### Post by Flareside on 2009-04-11
Just use AIM. You drag the file you want to send into the text box where you would type and hit enter. Me and my roomate use it all the time to share things like movies and tv shows, so it would definately work with the small file your talking about.

---

### Post by tomstealthports on 2009-04-11
Yeah, I must admit apache looks quite good.  

I can actually do port forwarding already.  I'm not too bad with iptables, and i can find out my ip address with ifconfig.

Well, that's certainly some useful suggestions from everyone.  I'll come back when I've tried them out a little bit.

Thank you all very much!

---

