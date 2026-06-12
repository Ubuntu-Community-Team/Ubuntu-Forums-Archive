---
title: "&quot;RED5&quot; &quot;need help with ports&quot; &quot;rtmp&quot; &quot;need sleep&quot;"
date: 2008-11-02
forum: Multimedia Software
---

### Post by ryry46d9 on 2008-11-02
we will start off with specs and get them out of the way

fresh install of ubuntu 8.10 server 32bit intell (head-less)

local network testing with another ubuntu box 8.04

looking to get "flash chat" installed on it after I get this fixed
[http://www.tufat.com/s_flash_chat_chatroom.htm](http://www.tufat.com/s_flash_chat_chatroom.htm)

built the latest java 6.0_10
built the latest ant 

 netstat -an | grep "LISTEN "
tcp        0      0 192.168.0.150:1935      0.0.0.0:*               LISTEN
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN

i have no 443 on the list but being how I think that is https im not worried

since it didn't work i followed  [http://osflash.org/red5/ubuntu804](http://osflash.org/red5/ubuntu804)
but changed (since I already installed them and /usr/lib/jvm/java-1.6.0-sun was a bad name)

export JAVA_HOME=/usr/lib/jvm/java-1.6.0-sun/
export ANT_HOME=/usr/share/ant/

to

export JAVA_HOME=/etc/java/jdk1.6.0_10/
export ANT_HOME=/etc/apache-ant-1.7.1/

all the demos seam to work but the port testing, it fails on rtmp 80 and 443,  besides all of rtmpt they say that don't work yet 

I tried ufw allow 80 and 443 and a few other ports I found along the way ,with no luck

I have spent the past 5 hours reading and playing 

I have played with so many different ideas I find my self repeating my self 

please point me in the right direction

---

### Post by ryry46d9 on 2008-11-04
ohhh come on  some one whats to tell me what I'm doing wrong

---

### Post by paranormalsos on 2009-02-01
I'm in the same boat as you :-) I'm trying to do the red5 just for the flash part of the flashchat I have the main chat hosted at my godaddy web hosting & I have made a server to make the video modules as a stand alone.  I too am having trouble with the porting & a few other areas. :-)

I'm at this stage too lol

"I have played with so many different ideas I find my self repeating my self

please point me in the right direction"

I'm also up for any help anyone can offer I really want to get the video & voice working in my chat rooms ;)

---

### Post by ryry46d9 on 2009-02-16
are you running F/C stand alone or with a CMS 

I got phpBB3 for my cms f/c 5X and I found a cool photo gallery mod for phpBB , but since I am not the brightest bean on the stock, I haven't got "profiles" to point out right 


Work in progress   big time 

I just did a fresh install  due to my error in SQL  (deleted the database) and gave 0.8 RC2 a run  same thing 

do you already have the A/V pack?, what OS are you running for the server,
I think you said your chat is hosted .... is red5 on that same box, 
(im running mine all out of my house)
 

, I'm dedicating  today to fix this problem since I got my A/V pack last night 

 I'll post later  today on a pass or fail

---

