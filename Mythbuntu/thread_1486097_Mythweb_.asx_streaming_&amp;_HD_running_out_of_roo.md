---
title: "Mythweb .asx streaming &amp; HD running out of room"
date: 2010-05-17
forum: Mythbuntu
---

### Post by winewood on 2010-05-17
Greetings,
 
I have some novice questions. I have attempted to browse forums for the fixes, I am not sure what to ask and I want to avoid breaking what is working. I have read the transcoding wiki and the mythweb wiki, but need these questions answered so I know which path to persue.
 
Question 1: Mythweb works for my configuration changes and scheduling. However I am unable to stream an .asx file. I am getting permission errors when I try to login via Windows Media Player and GOM Media player. I CAN stream to my PS3 (although I am not sure why or how its doing it). What do I need to clear fix permissions when streaming .asx files? I am unable to use my box logins or mythweb username and passwords.
 
Question 2: I am transcoding as I had belived that I needed to view via PS3 or remotely and get this commercial skip feature working or even playing off the frontend. I now have recorded shows (7 - 8 ) for one day and have taken up 104G of a 200G hard drive. This isn't realistic. What do I need to turn off? I even see some programs that were taped that I did not ask to tape. These show on the PS3 list, but not on my mythweb recorded program list. :confused:

---

### Post by winewood on 2010-05-20
Advice on where to look would be very helpful.  Anyone?

---

### Post by ian dobson on 2010-05-21
Hi,

Not sure about your permissions problem, but mythtv supports upnp as a server and your PS3 supports upnp as a client so they can "talk" to each other.

Regards
Ian Dobson

---

### Post by winewood on 2010-05-22
Thanks Ian! ...
I have my PS3 streaming working and its very cool for sure. 
 
Any ideas on the .asx permission issue?  how would one set a username and password wot see that via http and mythweb???  I can login to mythweb already, so the password on mythweb doesnt work in the authentication of username and pw.
 
As for space on my HD.. I see the files being transcoded.. so space is getting better as it sits around.. the commercials are still in the files that I download from the mythweb (non .asx), so it seems this "feature" isnt working even though my flag is showing that they were marked.

---

### Post by ian dobson on 2010-05-24
Hi,

OK i've just tried watching a asx stream through mythweb. My mythweb is password protected, so when I go the main mythweb page it asks for a password. I can then surf around mythweb without being asked for a password again. When I click on a link to a asx stream a media player program starts (vlc in my case) and requests the login name/password and the starts playing the video.

Apache allows individual directorys to be password protected using a .htaccess file, so it looks as if you mythweb isn't protected but the webweb/pl/stream is. Firstly go to the terminal prompt and type locate .htaccess This will show all files with the name .htaccess on your harddisks.

Now have a look in these files (hopefully it won't be too many) for something like:-
AuthName "MythTV"
AuthType basic
AuthUserFile /bla/bla/.htpasswd
require valid-user

the .htpasswd contains a list of the users/passwords.

Also what media play are you using so play the asx streams?

Regards
Ian Dobson

---

### Post by winewood on 2010-07-06
Ian, I appologize for not responding earlier. My notifications were turned off on when people replied.
 
Yes you were right, the security wasn't enabled for my folders. You suggestion will work and after playing around I decided on a bit more sercure meathod using htdigest from the instructions here [https://help.ubuntu.com/community/MythWeb](https://help.ubuntu.com/community/MythWeb)
 
I can now stream my music and it works great. For a time current Windows Media player played these great for anything that is still recording.  Once its recorded, it stops streaming.  Im guessing its chaning the permissions or something when it re-encodes it??  Im still investigating... strange.
 
I also answered my own question for the space issues I was having. If I view my recorded programs in MythWeb and go to LiveTV, the unit is now recording everything i can that is playing on the recorder. If this is left say, all day.. every show it plays will be recorded to the hard drive. This takes up ALL my space and I now know its a "feature" and not a curse as it will delete what it doesn't need. I seriously need to buy a 1.5 or 2 TB hard drive to suppliment this thing. [http://www.mythtv.org/wiki/LiveTV](http://www.mythtv.org/wiki/LiveTV)

---

### Post by ian dobson on 2010-07-06
Hi,

No problems, you wanted help from me, not the other way round.

I how have 6 2Tb drives in my backend server and already have used 50% from the space ;)

Regards
Ian Dobson

---

### Post by winewood on 2010-07-06
Your the best Ian..
 
I found out that I had 2 things keeping me from streaming everything on my computer.
 
I have 2 windows 7 PC's that I am streaming too.
*Windows security settings* or something is keeping 1 computer from streaming the .asx files.   My wifes laptop works FINE.  Horray for me and the random setting I changed somewhere.  They play great in WMP when they arent blocked.
 
I found a limitation that appeared as a "codec" issue.
It seems there is a limit on streaming *anything over 3.5 gig* files.  So anything over 30 minutes in size I cannot stream.  If it is under that, it works fine.  
 
Musings:  If the program is streaming in Standard Definition, does/can MythTV save them in an appropriate setting?  Can I designate a channel as SD to enable that flag?  Therefore the program should be much smaller when recorded.

---

### Post by winewood on 2010-08-18
Solution to appropriate sized recordings.
 
When you subscribe to a channel listing service, your format will be determined by the guide.  The box will record in an appropriate size automatically.
 
As for space concerns, when you leave your channel "watching tv", each program will be recorded in its entireity.  This allows for the user to come into a channel later and press record and get the entire program.  This live tv will expire faster than programs.  Therefore if you have 1 TB or 10 TB, eventually it should all fill up over time.  This will not be a problem, as it will use "auto-expire" to free up space.  Therefore expect a full hard drive.  
 
Streaming larger than 3-4GB files using "download .asx" is still not solved.

---

### Post by ian dobson on 2010-08-19
> **winewood said:**
> Solution to appropriate sized recordings.
 
When you subscribe to a channel listing service, your format will be determined by the guide.  The box will record in an appropriate size automatically.
 
As for space concerns, when you leave your channel "watching tv", each program will be recorded in its entireity.  This allows for the user to come into a channel later and press record and get the entire program.  This live tv will expire faster than programs.  Therefore if you have 1 TB or 10 TB, eventually it should all fill up over time.  This will not be a problem, as it will use "auto-expire" to free up space.  Therefore expect a full hard drive.  
 
Streaming larger than 3-4GB files using "download .asx" is still not solved.

I what are you streaming to? I've just tested streaming a 10Gb HD recording to vlc running on Windows7 and it worked without any problems.

You know that a asx is nothing more than a xml file that holds title/description/link to file ([http://etc](http://etc) or c:\bla bla).

if your trying to download the stream and save it to a disk, what format is the disk? If it's windows/fat32 your limited to 4Gb-1Byte.

Regards
Ian Dobson

Regards
Ian Dobson

---

### Post by winewood on 2010-08-19
Ian,
 
As always I appreciate your responses. I borrowed this screenshot to show where I am going.
[http://www.pdscc.com/troubleshooting/mythweb.jpg](http://www.pdscc.com/troubleshooting/mythweb.jpg)[]("http://jason.roysdon.net/wp-content/uploads/2009/03/screenshot-mythweb-recorded-programs-mozilla-firefox-300x156.png")
 
When I go into "Recorded Programs" the program picture is on the left. The top button to the upper right corner of that picture, the green icon. (I can "download" it using the white button below it.) However the green button is great as I can pop it up in Windows Media Player and it streams like im in front of the TV. This green one is limited to files that are 4 Gig and lower. 
 
Are you telling me you can get that green button working for large programs too? This limit is also present on my other Win7 laptop on the same network. 
 
My file system on my unix box is ext4, and my windows box is NTFS.

---

### Post by ian dobson on 2010-08-19
Hi,

I'm getting a forbidden for your link :(

Yes, when I click on the upper link (asx stream) vlc starts and plays the video no problems.

It sounds alot like a bug in Windows Media Player (no that can be, can it).

Could you try saving the asx file to the disk. Then open it in notepad and look for the line <REF HREF = and try opening the file defined ([http://192.168.0.1:80//mythweb/pl/strea/ZZZ/YYY](http://192.168.0.1:80//mythweb/pl/strea/ZZZ/YYY) with internet explorer. If this works then we know that the server/mythweb is OK. If this works try installing vlc and try opening the asx link.

Regards
Ian Dobson

---

### Post by winewood on 2010-08-19
I will try using your solution tonight!  Thanks.. 
I fixed the link.. :  [http://www.pdscc.com/troubleshooting/mythweb.jpg](http://www.pdscc.com/troubleshooting/mythweb.jpg)

---

### Post by winewood on 2010-08-19
VLC works.  
 
WMP doesn't.  Who would have thought??  :popcorn:  Thank you!

---

### Post by ian dobson on 2010-08-19
Hi,

So we've found a bug in wmp :D 

So just download the source code, patch it to support >4Gb files and compile. Don't forget to release the changes back to the community. Oh **** sorry this is microsoft, so go crying to them about it and maybe one day their going to fix is in Windows8/9.

Yes I love open source.

Regards
Ian Dobson

---

### Post by LowSky on 2010-08-20
just to mention commercial flagging. It doesn't actually delete the commercials. Just marks there locations for MythTV use.

See this link for help regarding removal, halfway down is a tutorial for automatic removal
[http://www.mythtv.org/wiki/Removing_Commercials](http://www.mythtv.org/wiki/Removing_Commercials)

---

