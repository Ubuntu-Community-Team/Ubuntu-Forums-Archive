---
title: "Extracting CDs to Server"
date: 2007-12-01
forum: Multimedia &amp; Video
---

### Post by Deronius on 2007-12-01
I tried with all my might to find solutions to my issue I couldn't find any.

I'm trying to extract CDs while encoding to mp3 to my server using Sound Juicer or any other ripping program.

Sound Juicer works just fine if I extract them to my local machine but when I try to point it to my server I get this message:  Sound Juicer could not extract this CD. Reason: Invalid parameters

Grip will work fine except for the life of me I cannot find where to direct it to my server.  I've configured it to covert to mp3 but I cannot find where to change the settings of the destination folder.

Goobox is perhaps the simplest and lightest weight of all of them.  It's simple to direct to my server folder and it works except I can't seem to find a way to encode it to mp3.

I'd love to not deal with mp3 but the rest of my family use players that require it.

If anyone has a solution to any of the 3 issue above I would be grateful to you.

~deronius

---

### Post by scxtt on 2007-12-01
how are you directing it to your server?

---

### Post by Deronius on 2007-12-01
For both Sound Juicer and Goobox I select it from the edit>preferences>folder.  I've mounted the the server folder I want to extract to.  I haven't directed Grip because I haven't figured it out yet.

~deron

---

### Post by scxtt on 2007-12-01
so you can't save to NFS?

---

### Post by Deronius on 2007-12-01
Mmm...I'm not sure I understand the question.

I extract just fine to my local machine.  I can extract to the server with Goobox just fine but I don't have a mp3 option.  I can extract to the linux server from my wife's windows machine.  I can't extract from my ubuntu laptop using Sound Juicer or Grip.  Sound Juice will extract to my laptop just fine but won't when I try to direct it to the server.  Grip won't because I don't know how to direct it to the server.

I hope that clarifies the issue a bit.

Thanks for the response.

---

### Post by scxtt on 2007-12-01
well, here's the setup i'm envisioning you have:

box1 (client): has sound juicer / grip / goobox on it and CD in drive waiting to be ripped
box2 (server): basically, just a networked "storage" box

what i'm saying (or wondering) is if you've created a NFS share on "server" and exported it, then mounted it on "client" ... so when you're ripping, you just use a path relative to the "client" box that IS your NFS share ... so when the rip is complete, the files are technically stored on "server" because that's where "client" saved them (via NFS) ...

are you familiar w/ NFS? (don't want to insult your intelligence :))

---

### Post by Deronius on 2007-12-01
I believe the answer is yes.  I have created shared folders on the server and I have mounted it to my laptop machine.  I'm able to extract to the server just fine using Goobox and from the lonely Windows machine using Media Player.  However, I will make no claims that I'm an expert in NFS.  This was my first server setup so it's more than possible that I missed something.  

Don't worry about insulting my intelligence.  I have a very hard head :)

---

### Post by scxtt on 2007-12-01
overall, is this what you're wanting to accomplish?:

get your ripped mp3s on the server.

is there a particular reason that when they're ripped, they HAVE TO be written to the server initially?  i ask cause of this statement: "Sound Juicer works just fine if I extract them to my local machine but when I try to point it to my server I get this message: Sound Juicer could not extract this CD. Reason: Invalid parameters" ...

can't you just rip them all to your laptop, them move them over?

---

### Post by Deronius on 2007-12-01
Oh certainly.  In fact, that is what I'm doing now...it just bothers me because I feel like I should be able to extract straight to the server while encoding to mp3.  It'll gnaw at me because I think I missed something in the set-up.  

I'll keep working at it until I get it or they carry me off to the insane asylum.

Again, thanks for the help.

---

