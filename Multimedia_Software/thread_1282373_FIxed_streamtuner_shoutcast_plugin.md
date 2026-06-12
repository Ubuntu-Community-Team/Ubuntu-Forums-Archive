---
title: "FIxed streamtuner shoutcast plugin"
date: 2009-10-04
forum: Multimedia Software
---

### Post by danny6167 on 2009-10-04
Im really sorry i couldn't find a better place to put this. (mods move if wanted)
Didn't find a real fix for this on the net so me and a mate spent some time looking at stream tuner.

Turns out the 2 problems with streamtuner in jaunty are simple as all hell.

1. It can't find ANY servers
Cause: Website was updated and doesnt fit the old format.
Fix: change shoutcast.com to classic.shoutcast.com in the src

2. Doesn't show category listed on the side.
Cause: Tabs were replaced with spaces on the page.
Fix: Replace \t with the correct spaces in the src.

I made the changes and uploaded it to my PPA. Im new to packaging so I don't know if it package metadata is correct. But what I do know is this is working for me and my mate.

[https://launchpad.net/~danny6167/+archive/ppa](https://launchpad.net/~danny6167/+archive/ppa)
[http://ppa.launchpad.net/danny6167/ppa/ubuntu/pool/main/s/streamtuner/](http://ppa.launchpad.net/danny6167/ppa/ubuntu/pool/main/s/streamtuner/)

Would recommend downloading and installing the .deb manually. God knows what i might upload to ppa later :)

Feedback Please:guitar:

---

### Post by bluebyt on 2009-11-01
Thanks you for this!

For me I have other problem with Streamtuner it always crashing when I click to select a radio.

---

### Post by yager01 on 2009-11-05
I had the same issue with the crashes after applying the patch.

The solution is to correct the preferences for which program to launch listening.

Go to Edit>Preferences>Applications and correct "Listen to a .m3u file" and "Listen to a stream"

I just upgraded to 9.10 so the sound program I have is Audacious2.  In my case both lines read as ```
audacious2 %q
```

Go to Applications>Sound&Video and check what programs you have available to play back the sound file.  Modify the above line to the name of your program followed by the %q and you should be ready to roll.

Remember to quit Streamtuner so it saves your settings.  When Streamtuner crashes out, your modifications do not get saved.

BTW, Danny you ROCK!!!  I have been searching for a patch on Streamtuner for a year.  I have not found a suitable replacement and it is great that you implemented the correction.  I had accomplished the first patch but could not figure out the solution to the second issue of the tabs.

---

### Post by danny6167 on 2009-11-11
Good catch yager01.
The crash is indeed caused but the expected player not existing in 9.10.

However, audacious2 still hated me after setting streamtuner to use it.
I just ended up just setting it as VLC.

Isn't the a program that opens files in the "Default" application. Would it be better to use this?


[http://pctoolbox.com.au/danny6167/blog/2009/10/09/7/fixed-streamtuner/](http://pctoolbox.com.au/danny6167/blog/2009/10/09/7/fixed-streamtuner/)

---

### Post by bluebyt on 2009-11-11
Thanks yager01, the crash seem to be solved!

Although i have another problem, Audacious is taking long time to open.
Error message : id3_file_vfsopen: file failed

Finally I installed xmms that solved the problem.

xmms:
[http://www.taltan.fr/post/2009/03/28/Pour-les-nostalgiques-de-XMMS-1.XX-sous-Ubuntu-la-suite]("http://www.taltan.fr/post/2009/03/28/Pour-les-nostalgiques-de-XMMS-1.XX-sous-Ubuntu-la-suite")

---

### Post by danny6167 on 2009-11-12
Yes, this is the same thing i saw but it never opened for me.
Probably would of in time knowing how impatient I am. :P
Thats why I just used VLC.

---

### Post by FornhamFred on 2009-12-17
Danny

I have downloaded your fix and also changed the preferences to Audacious2.

I am able to listen to streams in Xiph but still cannot list the shoutcast streams.

I am running Mint 8 based on 9.10.

Any help would be appreciated.:(:(

---

### Post by VastOne on 2009-12-17
Thank you Danny for this fix and to all those who helped.

I am using audacious2 on Koala and both it and stramtuner shoutcast are perfect again

Thank you!

---

### Post by wjston on 2009-12-24
> **FornhamFred said:**
> Danny

I have downloaded your fix and also changed the preferences to Audacious2.

I am able to listen to streams in Xiph but still cannot list the shoutcast streams.

I am running Mint 8 based on 9.10.

Any help would be appreciated.:(:(

Open a terminal - sudo gedit /etc/hosts

Add the following to the end of the file & save: 
#Streamtuner
205.188.234.120 [www.shoutcast.com](www.shoutcast.com)

---

### Post by danny6167 on 2009-12-26
@wjston
No, My patched version is configured to use the classic.shoutcast.com site by its self. No need to mod the hosts file.

@FornhamFred
It should work fine in mint. But I will see if I can test it my self when I get a chance.

---

