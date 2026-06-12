---
title: "Schedule Internet Radio Recordings?"
date: 2011-01-22
forum: Multimedia Software
---

### Post by klausner on 2011-01-22
Is there a way to schedule recordings of Internet Radio streams? I found [this thread]("http://ubuntuforums.org/showthread.php?t=413166") using cron and Streamripper, but I'd like to find a package that has all the support in one wrapper.
[IMG]http://www.onlinemarktplatz.de/wp-content/imagemanager/Smileys/smiley_frage.jpg[/IMG]

---

### Post by Cheesehead on 2011-01-25
You're asking for a car and a boat in one package. It's doubtful that many volunteer developers would spend their time recreating the cron and streamripper functionality to make such a specialized package.

This is one of the big differences between the Windows/Mac world ("there's an app for that") and the Linux community ("put the pieces together your way").

We can show you how to put the pieces together so it works beautifully. If you want us to.

---

### Post by klausner on 2011-01-25
> **Cheesehead said:**
> You're asking for a car and a boat in one package. It's doubtful that many volunteer developers would spend their time recreating the cron and streamripper functionality to make such a specialized package.

This is one of the big differences between the Windows/Mac world ("there's an app for that") and the Linux community ("put the pieces together your way").

We can show you how to put the pieces together so it works beautifully. If you want us to.

Why is it a car and a boat? I'm asking if there is a Linux equivalent of the DVR for radio, which is certainly a commodity item these days.

---

### Post by Cheesehead on 2011-01-25
From the lack of packages available to do that, and from the lack of other responses to your query, my estimate for such a demand may be lower than 'a commodity item'

I've looked through the packages in the Ubuntu Repositories (using the command 'apt-cache search record stream'), and I didn't find anything with a built-in timer. Since 'at' for scheduling a one-time job, and 'cron' (or the gui version, gnome-schedule) for multiple jobs, are very easy to use, that's not surprising.

In the Linux community, you are expected to put the pieces together like legos. It's one of the great strengths of the operating system and the community. And we're happy to help you do that. We were all new once, and we all remember what the learning curve is like!


First, 'at' and 'cron' are already installed on your system. To install streamripper: ```
sudo apt-get install streamripper
```

Second, to use 'streamripper', see the [man page]("http://pwet.fr/man/linux/commandes/streamripper")
You need to figure out all the elements you need (URL, length, save-to location) and then test it. It needs to work correctly before moving to the next step (time-shifting).
For example, the following command will record a stream for one hour and save it to a custom location:
```
streamripper http://stream-origin-URL -l 3600 -d /home/USER/custom-location
```


Third, time-shifting is actually much easier than figuring out the right streamripper commands...and that wasn't too hard, was it?
All the timeshifter does is run the command at the time you specify. Easy!

You can use 'at' for a simple one-time job:
```
at 15:30   (hit RETURN)
at> streamripper http://stream-origin-URL -l 3600 -d /home/USER/custom-location    (hit RETURN)
at>          (hit CTRL+D to end)
job 1 at Tue Jan 25 15:30:00 2011    (System response)

```

Alternately, use 'cron' for multiple jobs. Cron can be tricky - see the [cron tutorial]("http://www1.ubuntuforums.org/showthread.php?t=102626"):
Use the 'crontab -e' command to see and edit your crontab.
Add a line that looks like this to record at 15:30 every day: 
```
30 15 * * * streamripper http://stream-origin-URL -l 3600 -d /home/USER/custom-location
```


If you run into problems, let us know!
We are here to help!

---

### Post by klausner on 2011-01-25
> **Cheesehead said:**
> From the lack of packages available to do that, and from the lack of other responses to your query, my estimate for such a demand may be lower than 'a commodity item'


The kind of solution you note is exactly what was described in the thread I referenced in the original post. And not what I was looking for.

There must be others who have wanted to time-shift radio shows that are not available as podcasts. So I'm still in hopes of a unified solution. Hopefully someone can provide a pointer.

---

### Post by bill-lancaster on 2011-02-08
Have just seen your post.  I'm working with get_iplayer to listen to past BBC progs.  It aslo has a pvr function.

---

