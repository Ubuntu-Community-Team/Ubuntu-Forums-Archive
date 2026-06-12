---
title: "Not getting schedules from Scheduls Direct"
date: 2008-01-26
forum: Mythbuntu
---

### Post by dwf_starband on 2008-01-26
I set up mythbuntu in october, got a SD account and everything worked great.  Untill about the beginning of the year when it stoped getting schedualing.  I havent had much time to work on it, but it is pretty frustrating for both me and my wife(who was against the idea in the first place)

I had mythfilldatabase set to run automaticly, but even when I tried to run it manually I got errors.

HTTP request sent, awaiting responce... 401 unauthorized

Failed writing HTTP request: Bad file descriptor.

I contacted SD about it and they asked me to verify that i was getting the schedualing from them by following the instructions at, [http://forums.schedulesdirect.org/viewtopic.php?f=6&t=295](http://forums.schedulesdirect.org/viewtopic.php?f=6&t=295)

I followed those instructions and succesfully retrieved the schedualling from them.

I thnk this means that the fault is with my computer, mythbuntu, or the database.

I have tried,

mysqlcheck --repair -umythtv -p mythconverg

but that changed nothing.

I tried changing my SD account name and password which was suggested somewhere, but that didnt help either. (My user name had/has an underscore but trying without didnt matter)

I deleted the video source in mythbackend setup and tried starting with a fresh video source.  I enter in my user ID and password and press Retrieve Linups but it fails to retrieve(the same errors show in the terminal)

Do I need to compleatly start from the beginning and reinstall everything?
Is there a solution which would allow me to keep the recordings I already have?

Any Ideas or links to how-tos that I havent already tried would be appreciated.(Ive tried alot)

Thanks for your help,

Dennis

---

### Post by dflipb on 2008-02-19
do you have the latest version of mythtv? Because there was an update that helped fix that problem.

---

### Post by dwf_starband on 2008-02-21
ive got version 0.20.20070821-1 14283

how do I know what the latest version is and do I just install it over my existing one?

thanks for your help,

dennis

---

### Post by dflipb on 2008-02-22
you can check the latest version by going to mythtv.org and seeing what the latest download version is.  That is how I check.

But the site that helped me get things going was
 
[http://www.mythtv.org/docs/mythtv-HOWTO-24.html#ss24.4](http://www.mythtv.org/docs/mythtv-HOWTO-24.html#ss24.4)

this helped clear up why it wasn't downloading for me. and the 401 error is what it usually says, and is not a concern.

---

### Post by dwf_starband on 2008-02-23
I downloaded the latest mythbuntu 8.4Alpha and tried with it and still cant get the schedules from SD.  I even tried a new trial account with a different email and it doesnt work either.  I spent some time in irc tonight and the guy I was talking to thought it might be internet/network related but wasnt sure.

Any more Ideas?

dennis

---

### Post by dflipb on 2008-02-23
what are your hardware specs?  Do you have more than one tuner?

---

### Post by dwf_starband on 2008-02-23
just one tuner, WinTV-PVR-150

im not sure how the tuner effects the schedual retrevial?

it had worked great for a few months, it actually still works if i manually change channels on the satalite box, but that sort of defeats the purpous of the whole thing.

thanks for your help, any more ideas would be great,

dennis

---

### Post by dflipb on 2008-02-23
in your SD account, what do you have as your standalone program when you click on edit account details.

I have in XMLTV: MythTV/XMLTV not Mythbuntu.

---

### Post by dwf_starband on 2008-02-23
I just tried that and there was no difference. here is the output when i try to retrieve lineups in video source setup,

[http://pastebin.com/f5a8df034](http://pastebin.com/f5a8df034)

dennis

---

### Post by dflipb on 2008-02-23
in your backend setup of the card, make sure to have the xmltv checkmark on.

---

### Post by dwf_starband on 2008-02-23
where in the backend setup is the xmltv setting?

thanks,

dennis

---

### Post by dflipb on 2008-02-24
I just updated to mythbuntu 8 and they changed the backend interface =\ so I'm a bit lost with this version..

But I did come across this

[http://www.mythtv.org/wiki/index.php/Troubleshooting:mythbackend:_Problem_with_capture_cards:_Card_1failed_init](http://www.mythtv.org/wiki/index.php/Troubleshooting:mythbackend:_Problem_with_capture_cards:_Card_1failed_init)

maybe that can help you.

---

