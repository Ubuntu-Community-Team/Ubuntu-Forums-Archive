---
title: "Lost Schedule Direct updates - everything &quot;unknown&quot;"
date: 2008-05-05
forum: Mythbuntu
---

### Post by jmverner on 2008-05-05
My network was down yesterday for a few hours.  After it came back up I found that all Program Guide data was missing.  I rebooted thinking that would force the backend to reread the data but it did not.  I waited 24 hours thinking that the scheduler would automatically resync but that did not work either.  What else can I do to force the backend to refill the database from Schedule Direct?
Thanks.

---

### Post by mythpeterp on 2008-05-05
You can manually fill the database by running "mythfilldatabase" from a console window. That will not permanently fix the problem, but will at least be a short term fix until you can figure out why it is not updating..

---

### Post by jmverner on 2008-05-05
That did it - thanks for the quick reply.
How does one go about figuring out what the original issue was in case it does not read again?  Are there logs or something I can look at?
Thanks again.

---

### Post by tgm4883 on 2008-05-05
You can check the logs at /var/log/mythtv/mythbackend.log on your backend.  Also, in your frontend setup, make sure that you have setup mythfilldatabase to run

How long have you had the system installed?

---

### Post by jmverner on 2008-05-07
It was up about a week when I lost the SD info.

I do not see any configuration in the frontend setup (Control Centre) for forcing mythfilldatabase to run.  Can you give a pointer please?

I also ran the backend setup and no go there either.  It did ask at the end before exiting if I wanted to do the fill.

---

### Post by tgm4883 on 2008-05-07
> **jmverner said:**
> It was up about a week when I lost the SD info.

I do not see any configuration in the frontend setup (Control Centre) for forcing mythfilldatabase to run.  Can you give a pointer please?

I also ran the backend setup and no go there either.  It did ask at the end before exiting if I wanted to do the fill.

Sounds like your problem.

In the frontend, go to "Ubilities / Setup", "Setup", "General" then on the last screen (should be the 7th screen) it says "Automatically run mythfilldatabase".  Check that box, then at the bottom also check "Run mythfilldatabase at time suggested by the grabber".  Then if you wait 24 hours it should run and you should have the data again (and it will continue to run daily)

---

### Post by jmverner on 2008-05-10
Absolutely!
Not sure how I missed that looking earlier.
Many thanks.

---

