---
title: "Unity MythTV Scope - Testers needed"
date: 2012-04-19
forum: Mythbuntu
---

### Post by tgm4883 on 2012-04-19
I'm looking for some testers for a Unity scope I wrote for MythTV.
More information is on our website at [http://www.mythbuntu.org/unity-scope-mythtv](http://www.mythbuntu.org/unity-scope-mythtv)

You can send feedback here or in our IRC channel #ubuntu-mythtv-dev

Version 1.1
Grab it here [https://launchpad.net/~mythbuntu/+archive/testing/+build/3439140/+files/unity-scope-mythtv_1.1-0ubuntu1_all.deb](https://launchpad.net/~mythbuntu/+archive/testing/+build/3439140/+files/unity-scope-mythtv_1.1-0ubuntu1_all.deb)

Features added in 1.1
* Icons now show coverart (if available) instead of generic video icon
* Items in MythVideo now available for playback

---

### Post by utillich on 2012-04-20
First off: Thank you for this, you guys rock! 

I just installed it and tested for a couple of recordings. Aside from getting [this bug]("https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/510376") it works great.  Will report in more detail once I have had time to test it more extensively. 


One question: Is it planed for future releases to also access videos (from myth-video). I have few recordings, but an extensive media library in myth-video, so I would love that functionality.

---

### Post by tgm4883 on 2012-04-20
> **utillich said:**
> First off: Thank you for this, you guys rock! 

I just installed it and tested for a couple of recordings. Aside from getting [this bug]("https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/510376") it works great.  Will report in more detail once I have had time to test it more extensively. 


One question: Is it planed for future releases to also access videos (from myth-video). I have few recordings, but an extensive media library in myth-video, so I would love that functionality.

I hadn't planned that, but it shouldn't be that difficult to add. I'll look at the API a bit next week (moving this weekend).

---

### Post by williammanda on 2012-04-22
Can this be tested on desktops that have Mythfrontend installed?

---

### Post by tgm4883 on 2012-04-22
> **williammanda said:**
> Can this be tested on desktops that have Mythfrontend installed?

Yes. On desktops that have mythfrontend installed, it will play in the mythavtest program. This will give you commercial skipping capabilities, but currently doesn't work so well with compiz. (doesn't fill the screen properly)

---

### Post by tgm4883 on 2012-04-28
> **utillich said:**
> First off: Thank you for this, you guys rock! 

I just installed it and tested for a couple of recordings. Aside from getting [this bug]("https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/510376") it works great.  Will report in more detail once I have had time to test it more extensively. 


One question: Is it planed for future releases to also access videos (from myth-video). I have few recordings, but an extensive media library in myth-video, so I would love that functionality.

Uploading version 1.1 now that allows playback of Videos in the Videos Storage Group. For some reason, mythavtest cannot playback things from the Videos Storage Group (see MythTV bug [http://code.mythtv.org/trac/ticket/10666](http://code.mythtv.org/trac/ticket/10666) )

---

### Post by tgm4883 on 2012-04-29
> **tgm4883 said:**
> Uploading version 1.1 now that allows playback of Videos in the Videos Storage Group. For some reason, mythavtest cannot playback things from the Videos Storage Group (see MythTV bug [http://code.mythtv.org/trac/ticket/10666](http://code.mythtv.org/trac/ticket/10666) )

Sorry for the delay, looks like the new build (1.1-0ubuntu1) will be up in about 15 minutes with the above bug resolved.

---

### Post by dakota34 on 2012-05-13
hi there, I've installed per the instructions and after a reboot I see the mythtv lens, but nothing comes up in recorded shows or videos. I've set it up on a machine that runs a slave backend and a frontend

---

### Post by tgm4883 on 2012-05-14
> **dakota34 said:**
> hi there, I've installed per the instructions and after a reboot I see the mythtv lens, but nothing comes up in recorded shows or videos. I've set it up on a machine that runs a slave backend and a frontend

Can you check if the following file exists and has your correct backend information in it?

```
~/.mythtv-scope-location.conf
```

---

### Post by dakota34 on 2012-05-14
I've checked, and I don't have a  .mythtv-scope-location.conf in my home directory. Should I create one?

---

### Post by tgm4883 on 2012-05-14
> **dakota34 said:**
> I've checked, and I don't have a  .mythtv-scope-location.conf in my home directory. Should I create one?

No, don't create it yet. After installing the package did you reboot the machine?

Try running

```
ps aux | grep mythtv
```

and post the output here.

---

### Post by dakota34 on 2012-05-14
here's the output:

[PHP]john@john-desktop:~$ ps aux | grep mythtv
mythtv    2080  2.5  1.5 1912108 60720 ?       Sl   21:28   0:03 /usr/bin/mythbackend --syslog local7 --user mythtv
john      2743  0.1  0.4 380752 20020 ?        Sl   21:29   0:00 /usr/bin/python /usr/lib/unity-scope-mythtv/unity-scope-mythtv
john      4058  0.0  0.0  13580   888 pts/0    S+   21:30   0:00 grep --color=auto mythtv
[/PHP]

---

### Post by tgm4883 on 2012-05-14
> **dakota34 said:**
> here's the output:

[PHP]john@john-desktop:~$ ps aux | grep mythtv
mythtv    2080  2.5  1.5 1912108 60720 ?       Sl   21:28   0:03 /usr/bin/mythbackend --syslog local7 --user mythtv
john      2743  0.1  0.4 380752 20020 ?        Sl   21:29   0:00 /usr/bin/python /usr/lib/unity-scope-mythtv/unity-scope-mythtv
john      4058  0.0  0.0  13580   888 pts/0    S+   21:30   0:00 grep --color=auto mythtv
[/PHP]

Ok, so it is running, but not finding the backend it seems. Run this

> /usr/lib/unity-scope-mythtv/mythtvapi.py

Then tell me if ~/.mythtv-scope-location.conf exists and has the correct info.

---

### Post by dakota34 on 2012-05-15
it looks like this:

[Backend]
location = [http://192.168.0.7:6544](http://192.168.0.7:6544)
mythprotocolport = 6543


which is the correct IP for the master backend.

---

### Post by josephmills on 2012-05-15
I am also very interested in this. 
I found out about this last night well surfing.
[COLOR="Red"]warning [/COLOR]
(I am v.new to myth)
I was wondering if there are any plans at all to kinda bring together 
[https://launchpad.net/ubuntutv](https://launchpad.net/ubuntutv)
with what you guys are awesomely doing at mythbuntu ? 
Once again I am real new too this.I don't even know if they could flow together. In fact I don't even know what a smart tv is. :) 
Thanks for taking the time too look over my question and I look forward to testing the scope. Thanks again 
Joseph

---

### Post by tgm4883 on 2012-05-15
> **dakota34 said:**
> it looks like this:

[Backend]
location = [http://192.168.0.7:6544](http://192.168.0.7:6544)
mythprotocolport = 6543


which is the correct IP for the master backend.

Ok, so it didn't generate that when running on it's own, but it did find the backend. Can you search the recordings now in Unity?

> **josephmills said:**
> I am also very interested in this. 
I found out about this last night well surfing.
[COLOR="Red"]warning [/COLOR]
(I am v.new to myth)
I was wondering if there are any plans at all to kinda bring together 
[https://launchpad.net/ubuntutv](https://launchpad.net/ubuntutv)
with what you guys are awesomely doing at mythbuntu ? 
Once again I am real new too this.I don't even know if they could flow together. In fact I don't even know what a smart tv is. :) 
Thanks for taking the time too look over my question and I look forward to testing the scope. Thanks again 
Joseph

I'm developing this scope with that in mind. My goal is to have it as something you can add and use with Ubuntu TV.

---

### Post by josephmills on 2012-05-15
> **tgm4883 said:**
> 
I'm developing this scope with that in mind. My goal is to have it as something you can add and use with Ubuntu TV.

That is so flippen awesome! I am going to join your Irc channel and watch how this moves. I think that it is really great times for Ubuntu This just added to the list of why I love *Ubuntu so much.

---

### Post by dakota34 on 2012-05-16
so I have MythTV Shows and MythTV Movies filters, but no shows or movies from Myth actually show up

---

### Post by tgm4883 on 2012-05-16
> **dakota34 said:**
> so I have MythTV Shows and MythTV Movies filters, but no shows or movies from Myth actually show up

If you go to the following link in a web browser, does it show you an XML listing of your recordings?

[http://192.168.0.7:6544/Dvr/GetRecordedList](http://192.168.0.7:6544/Dvr/GetRecordedList)

---

### Post by dakota34 on 2012-05-16
it gives me a list of recorded programs, very small excerpt here:

[HTML]ProgramList version="1.0" serializerVersion="1.1"><StartIndex>0</StartIndex><Count>817</Count><TotalAvailable>817</TotalAvailable><AsOf>2012-05-17T01:58:24</AsOf><Version>0.25.20120506-1</Version><ProtoVer>72</ProtoVer><Programs><Program><StartTime>2010-06-10T02:00:00</StartTime><EndTime>2010-06-10T03:00:00</EndTime><Title>Toddlers & Tiaras</Title><SubTitle>Director's Choice Pageant</SubTitle><Category>Reality</Category><CatType/><Repeat>false</Repeat><VideoProps>0</VideoProps><AudioProps>1</AudioProps><SubProps>1</SubProps><SeriesId>EP01119959</SeriesId><ProgramId>EP011199590035</ProgramId><Stars>0</Stars><FileSize>2159902656</FileSize><LastModified>2012-04-27T01:28:14</LastModified><ProgramFlags>5</ProgramFlags><FileName>2034_20100609220400.mpg</FileName><HostName>mythtv</HostName><Airdate>2010-06-09</Airdate><Description>Children compete in the Director's Choice Pageant in Paragould, Ark.</Description><Inetref>118021</Inetref><Season>3</Season><Episode>2</Episode><Channel><ChanId>2034</ChanId><ChanNum>34</ChanNum><CallSign>TLCCAN</CallSign>[/HTML]

---

### Post by tgm4883 on 2012-05-16
> **dakota34 said:**
> it gives me a list of recorded programs, very small excerpt here:

[HTML]ProgramList version="1.0" serializerVersion="1.1"><StartIndex>0</StartIndex><Count>817</Count><TotalAvailable>817</TotalAvailable><AsOf>2012-05-17T01:58:24</AsOf><Version>0.25.20120506-1</Version><ProtoVer>72</ProtoVer><Programs><Program><StartTime>2010-06-10T02:00:00</StartTime><EndTime>2010-06-10T03:00:00</EndTime><Title>Toddlers & Tiaras</Title><SubTitle>Director's Choice Pageant</SubTitle><Category>Reality</Category><CatType/><Repeat>false</Repeat><VideoProps>0</VideoProps><AudioProps>1</AudioProps><SubProps>1</SubProps><SeriesId>EP01119959</SeriesId><ProgramId>EP011199590035</ProgramId><Stars>0</Stars><FileSize>2159902656</FileSize><LastModified>2012-04-27T01:28:14</LastModified><ProgramFlags>5</ProgramFlags><FileName>2034_20100609220400.mpg</FileName><HostName>mythtv</HostName><Airdate>2010-06-09</Airdate><Description>Children compete in the Director's Choice Pageant in Paragould, Ark.</Description><Inetref>118021</Inetref><Season>3</Season><Episode>2</Episode><Channel><ChanId>2034</ChanId><ChanNum>34</ChanNum><CallSign>TLCCAN</CallSign>[/HTML]

Ok, so that is the right info it seems. I'm going to have you run it manually and see if any results are being seen.

If you run 

```
/usr/lib/unity-scope-mythtv/mythtvapi.py
```

Do any results pop up? By default it does a search for 'house' so should return results for any shows that have house in the title, subtitle or description.

You can also try running the whole scope manually, although it is a little more work.

1) Backup the dbus service file that starts the scope

```
sudo mv /usr/share/dbus-1/services/mythtv.service ~/mythtv.service
```

2) Reboot your desktop

3) Run the scope with

```
/usr/lib/unity-scope-mythtv/unity-scope-mythtv
```

---

### Post by dakota34 on 2012-05-17
okay, so when I run /usr/lib/unity-scope-mythtv/mythtvapi.py it returns a list of shows, but when I follow the instructions to run the scope manually, by moving the file, rebooting, then running  /usr/lib/unity-scope-mythtv/unity-scope-mythtv I get nothing when I click on 'MythTV shows' in the scope

---

### Post by tgm4883 on 2012-05-17
> **dakota34 said:**
> okay, so when I run /usr/lib/unity-scope-mythtv/mythtvapi.py it returns a list of shows, but when I follow the instructions to run the scope manually, by moving the file, rebooting, then running  /usr/lib/unity-scope-mythtv/unity-scope-mythtv I get nothing when I click on 'MythTV shows' in the scope

Are you just clicking on "MythTV shows" or are you also typing something in the search box?

---

### Post by dakota34 on 2012-05-18
I'm clicking on Mythtv Shows, then searching with a word from the title. But when I did it tonight I got a crash report detected message for the unity scope repeatedly, So I've removed and reinstalled myth-backend from this machine (slave) & rebooted & reinstalled using  sudo dpkg -i unity-scope-mythtv_1.1-0ubuntu1_all.deb, rebooted again, and now it's working. I'm wondering if I screwed something up when I put a secondary backend on my desktop.  Anyway thanks for all your help, this thing is great.

---

### Post by tgm4883 on 2012-05-18
> **dakota34 said:**
> I'm clicking on Mythtv Shows, then searching with a word from the title. But when I did it tonight I got a crash report detected message for the unity scope repeatedly, So I've removed and reinstalled myth-backend from this machine (slave) & rebooted & reinstalled using  sudo dpkg -i unity-scope-mythtv_1.1-0ubuntu1_all.deb, rebooted again, and now it's working. I'm wondering if I screwed something up when I put a secondary backend on my desktop.  Anyway thanks for all your help, this thing is great.

Glad to hear it's working. Putting a secondary backend on your desktop shouldn't have hurt anything but it isn't something I have tested. I'll test it now though :)

---

### Post by ahood on 2012-07-07
Installed the 1.1 version of this scope.

When I click on a recorded TV program, a prompt appears asking whether to play with movie player or download. Default is to play with movie player. If this is selected, the video is downloaded first instead of just playing. Is this intended?

Note: I can stream the recording using mythweb.

---

### Post by tgm4883 on 2012-07-07
> **ahood said:**
> Installed the 1.1 version of this scope.

When I click on a recorded TV program, a prompt appears asking whether to play with movie player or download. Default is to play with movie player. If this is selected, the video is downloaded first instead of just playing. Is this intended?

Note: I can stream the recording using mythweb.

Thats odd. Can you take a screenshot of the prompt?

---

