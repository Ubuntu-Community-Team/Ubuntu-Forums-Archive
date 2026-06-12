---
title: "youtube problem"
date: 2008-06-29
forum: Multimedia Software
---

### Post by robertchahine on 2008-06-29
Hi guys.After installing Hardy , everytime i wanna see a video on youtube, i get an error "This video is no longer available".
I was searching on google and the forum, i didn't found solutions.Someone said to clear private data, other said to start firefox as root(using gksudo), but didn't work.This is youtube problem , because when i open metacafe, i can see the videos, but not youtube.

---

### Post by pytheas22 on 2008-06-29
Does this happen with every video you try to watch (and not to be too obvious, but have you checked to make sure these videos can still be viewed on another computer)?

You might want to try installing a different browser to see if the problem still occurs.

If the problem is Firefox's fault, then:
```

mv ~/.mozilla ~/.mozila-OLD
```

should help.

---

### Post by robertchahine on 2008-06-29
> **pytheas22 said:**
> Does this happen with every video you try to watch (and not to be too obvious, but have you checked to make sure these videos can still be viewed on another computer)?

You might want to try installing a different browser to see if the problem still occurs.

If the problem is Firefox's fault, then:
```

mv ~/.mozilla ~/.mozila-OLD
```

should help.
yep, it's all youtube videos, and i can watch them on other machine.
And moving the folder didn't solve the problem, thx anyway for your reply

---

### Post by robertchahine on 2008-06-29
A lot of people found that the google web accelerator was the problem.But i don't have this add-on.By the way, youtube videos work great on opera, but still want to know why i have this problem on firefox(with firefox 3 beta 5 i watched a lot of videos).Is there another add-on that made a problem?

---

### Post by pytheas22 on 2008-06-29
Which other add-ons do you have?  You could try disabling them and see if it makes a difference.  You could also try an apt-get remove --purge firefox to see if it helps, but I don't know.  I guess it is clear, however, that the problem has to do just with Firefox, since it works in Opera.

---

### Post by robertchahine on 2008-06-30
even removing the configurations files of mozilla didn't solve the problem.
But i'm so impressed, yesterday, i disabled all add-ons, and youtube didn't work, but today,i disabled them again, and it's working like a charm.Wow, why that, i don't know :)

---

### Post by Kadrus on 2008-09-18
> This video is no longer available
Robert,this error message are from the Lebanese ISP,its very common and nothing to do with the OS.It usually appears if you are with VISP,
[YouTube: "We're sorry, this video is no longer available" and VISP!!]("http://www.lebgeeks.com/forums/viewtopic.php?id=5084")

---

