---
title: "Question about Live-TV"
date: 2008-05-02
forum: Mythbuntu
---

### Post by the[V]oid on 2008-05-02
Hi, I just wondered why MythTV permanently records shows I watch? I have recordings of shows that I watched three or four days ago, although I never explicitly used the recording functionality. Is there a possibility to avoid that? It would be perfect if MythTV wouldn't record anything except I order it. Thanks!

---

### Post by tgm4883 on 2008-05-02
You aren't watching live tv, you are watching tv that has been recorded to your hard drive.  To answer your question we need to better understand your hardware, what tv tuners do you have?

---

### Post by fenian on 2008-05-02
As well as functioning as a PVR Mythtv allows you to pause/play live tv,in order to do this it records the program first.I don't think you can change this as it is the main purpose of Mythtv.

From the official MythTv wiki...

>  Why is MythTV recording EVERYTHING I watch in Live TV?

MythTV is not your average TV. It's a digital video recorder! When you watch TV, the ability to pause, rewind, and skip commercials is because it is actually recording everything you watch. As an added bonus, when you are watching something and decide you want to keep it, hitting record will just tag the existing recording as a keeper. The LiveTV page has lots more info, but here are the three most FAQs.

But my Harddrive keeps filling up from all these Live TV recordings! How do I stop it from recording?

    * Short answer: You can't. 

    * Long answer: You can't stop it from recording, but you can stop it from filling up your harddrive. MythTV is designed with an autoexpire concept. Every time Myth tries to watch or record something, it first makes sure that it has room for it, and will delete the oldest available recording to make space. You can specify how much free space to leave, but it is recommended to dedicate a partition to Myth recordings and tell it to leave at least one gigabyte free. Live TV recordings by default have a shorter lifespan than normal recordings and a lower priority, so they will be expired before any recordings are. 


It didn't used to do this, why did it change?

    * It always did. In versions before 0.19, it saved live TV recordings to a separate file (a ring buffer), which stayed within a certain size range. It got complicated when you have more than one tuner and more than one live broadcast being viewed. There was no easy way to transfer from that ring-buffer file into a normal recording, so even though you can pause the TV, there was no way to keep it (and if you paused for long enough, another scheduled recording would come around and wipe out your live TV buffer). 


I don't want it to delete things unless I tell it to!

    * You have the option when recording a program to have it auto-expire or not, as well as the ability to change that setting on an individual-recording basis. If no programs are set to auto-expire, however, it will run out of space very quickly.

---

### Post by the[V]oid on 2008-05-02
> **fenian said:**
> As well as functioning as a PVR Mythtv allows you to pause/play live tv,in order to do this it records the program first.I don't think you can change this as it is the main purpose of Mythtv.

OK, I don't want to prevent MythTV from recording anything. But I want it to delete the recordings I have not ordered when it doesn't need them anymore.

> **tgm4883 said:**
> You aren't watching live tv, you are watching tv that has been recorded to your hard drive.  To answer your question we need to better understand your hardware, what tv tuners do you have?

I'm not sure whether this is what you asked for, but my TV-Card is: Cinergy 1200 DVB-S

---

### Post by fenian on 2008-05-02
To delete recordings in mythtv;

Go to the main menu screen (where watch tv option is) and select Manage Recordings option.From the next screen select Delete Recordings.On the next screen press  the 'm' key on your keyboard,choose change group filter and select LiveTV.Use the arrow keys to highlight selections and use the enter key to delete them.

---

### Post by shad0w_walker on 2008-05-02
The automaticly recorded (For the pause, etc functions on livetv) should be automatically deleted after 24 hours, sooner if the hard drive starts to become to full. It sounds like this is a weird bug that's managed to lose the auto expire option. I'd suggest you also have a look at the mythtv forums, they might be able to help somemore.

[http://www.mythtvtalk.com/forum/](http://www.mythtvtalk.com/forum/)

---

### Post by fenian on 2008-05-02
To set the auto expire for recordings go to the main screen,select Utilities/Setup,from the next screen select Setup,from the next screen select TV Settings,from the next screen select General.On the second screen in this sectio you can change the setings (see the screenshot attached)

---

### Post by shad0w_walker on 2008-05-02
Going just a little off topic, nice theme. Mind sending a link my way? :)

---

### Post by fenian on 2008-05-03
Actually its two themes.
I used the znivre theme (find it [here]("http://www.gnome-look.org/content/show.php/zniavre?content=72328")) for the main theme and I used the Slickness Black theme (find it [here]("http://www.gnome-look.org/content/show.php/Slickness+Black?content=73210")) for the window border (use the customize option in Appearancs prefs.)

---

### Post by tgm4883 on 2008-05-03
Just in case he was asking about the MythTV theme, that is the Mythbuntu theme in 8.04

---

