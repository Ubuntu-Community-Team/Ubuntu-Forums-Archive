---
title: "Openshot 2.0.6 will not open .OSP file created with version 1.4.3"
date: 2016-03-02
forum: Multimedia Software
---

### Post by KenUBF on 2016-03-02
Hello all,  I had a question about opening my backup .osp file of my video project that was created with an older version of Openshot, version 1.4.3., which I had installed from the Software Center.  After reinstalling my system recently Openshot would no longer open (it worked fine before the system reinstall). Sometimes the icon would flash but then, nothing. Couldn't find any useful info on making it work, especially since it wouldn't even open to provide any kind of error message. It simply stopped responding.   Anyhow, I just wanted to provide some background to my situation, and here is my question. I decided to install the newest version via the PPA's and this version, 2.0.6 opens just fine. However, this new version will not open my .osp video file that I had created with the older version. I get the following error when I try to open the files:  [php] Couldn't load project data file: Expecting value: line 1 column 1 (char 0) [/php]  What does this mean? Is there a possible fix? I am a bit frantic since I cannot lose this project. Thank you in advance for any help you can provide.   Note: I am running Ubuntu 14.04 LTS with all updates current.

---

### Post by s0urCr34m on 2016-03-05
Have you tried asking @ [http://openshotusers.com/forum/](http://openshotusers.com/forum/)

---

### Post by KenUBF on 2016-03-05
> **s0urCr34m said:**
> Have you tried asking @ [http://openshotusers.com/forum/](http://openshotusers.com/forum/)  Thanks for the reply. Yes, I did post a question on one of their forums but haven't heard back yet. The issue turns out to be moot anyway. I just found out earlier my project back up got corrupted in addition to the original issue. That's what I get for not backing up my back ups. Lesson learned. I'll just have to work from the earlier version I have saved and redo it. It will be major late, but at least it will get done. I will mark this as solved since it appears that someone can use the terminal to diagnose some issues. I typed in the terminal to run Openshot and it gave me a list of errors. I'm still new with Ubuntu so hopefully another newbie can learn from my mistake.

---

### Post by s0urCr34m on 2016-03-05
You're welcome. Just curious BTW, how do you like Openshot? I haven't tried it yet. Can it take a pounding or does it crash often? Have you tried Kdenlive? I hear Kdenlive is great, it sure is recommended by a lot of people. The other video editing projects I've tried randomly crash!

---

### Post by KenUBF on 2016-03-05
> **s0urCr34m said:**
> You're welcome. Just curious BTW, how do you like Openshot? I haven't tried it yet. Can it take a pounding or does it crash often? Have you tried Kdenlive? I hear Kdenlive is great, it sure is recommended by a lot of people. The other video editing projects I've tried randomly crash!  I do like Openshot. The version you can get from the repositories does crach quite often, particularly when you're working on a larger project with many files you're trying to put together and edit. Smaller files seem to do much better. If you use it make sure you use the auto back up feature and save often, which is very easy, just clicking a button at the top, and it saves your work. I have tried Kdenlive but it didn't seem to have the features I wanted. However, I didn't use it much so I can't say with much confidence if it's better than Openshot, but I guess it depends on your needs. I did install the most recent version of Openshot via the PPA's and I haven't used it yet to see if the same issue occurs. I will try to remember and update this reply to let you know.

---

### Post by s0urCr34m on 2016-03-05
Thanks for the reply. Please do let me know what your experience is like!

---

### Post by Linuxisfast on 2016-03-06
The version in 14.04 never ever crashed for me even when I used 1080p files. I have tried 4K files on Open Shot 2.0 and its been rock steady. System crashes come from codecs and drivers, if they are in order Open Shot is very stable. In Arch I find it less stable compared to Ubuntu and the AUR Open Shot 2.0 is not as good as the one from PPA.

---

### Post by KenUBF on 2016-03-16
> **s0urCr34m said:**
> Thanks for the reply. Please do let me know what your experience is like!  I agree with Linuxisfast. Openshot 2.0 is not very stable for me. It seems much worse at crashing then the one I originally had installed from the Software Center. I think I may just reinstall that one and hope it works ok. Or I can just wait for the Ubuntu 16.04 upgrade and hope Openshot 2.0 is more stable on that system.   All I was doing was doing a very fast edit with a small 10 mintute video and it crashed about 5 times. And the backup file seems pretty buggy too. It doesn't seem to save my work as well as the older version. If you want to try Openshot I would definitely try the one from the Software Center, and remember to back up your work often just in case.

---

### Post by Linuxisfast on 2016-03-16
Actually my experience is exactly the opposite. I have been doing some extensive editing with Openshot 2.06 and so far no crashes. My system is i7 4790 with 16gb RAM and nvidia GeForce 610. The nvidia is running driver 361.28 from graphics driver ppa.

---

### Post by KenUBF on 2016-04-14
Oops. Looks like I read your comments too fast. Sorry! I'm glad you're not having any issues. I will wait until the release of 16.04 to see if 2.0 is any more stable for me. I read that it works better with the newer version for some.

---

