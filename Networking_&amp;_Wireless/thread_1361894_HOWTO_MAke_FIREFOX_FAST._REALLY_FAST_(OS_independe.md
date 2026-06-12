---
title: "HOWTO: MAke FIREFOX FAST. REALLY FAST (OS independent)"
date: 2009-12-22
forum: Networking &amp; Wireless
---

### Post by linuxgeek77 on 2009-12-22
Here are teh steps to increase your firefox browsing experience as much as 50 - 60% Follow these steps closely and tell me/ report back how you feel about it. You will love it. 

1) In the address bar Type:   about:config (accept any warning and continue)
2) search (in the filter) for: pipelining
3) look for network.http.pipelining set it to TRUE (FALSE by DEFAULT) by double clicking it
4) look for  network.http.pipelining.maxrequests double click it and set the value to 150
5) if you use proxy then look for network.http.proxy.pipelining and double click it and set it to TRUE. 

Now after you do so close out FIREFOX and go back and type again about:config in the address bar and in teh configurations ADD the following strings (right click anywhere on any value > then go to NEW > then go to STRING) and set the values for both of these new strings to 0.

nglayout.initialpaint.delay       

content.notify.interval                

Remember to set the value to 0 for both of them. a popup will appear and will ask you for a value .. put  a 0 "ZERO"

Close out firefox and Reopen IT and tell me how fast it went for you. it performs 60% faster for me. even faster than GOOGLE CHROME (by alot)

---

### Post by linuxgeek77 on 2009-12-22
[http://www.youtube.com/watch?v=rCKffUtkfLw](http://www.youtube.com/watch?v=rCKffUtkfLw)

Here is a video tutorial on how to do it. I hope i helped someone.

---

### Post by coffeeandlinux on 2009-12-30
Worked like a charm! Firefox runs at least 10 times faster.

---

### Post by Abhijit Navale on 2010-03-06
> **linuxgeek77 said:**
> 

1) In the address bar Type:   about:config (accept any warning and continue)
2) search (in the filter) for: pipelining
3) look for network.http.pipelining set it to TRUE (FALSE by DEFAULT) by double clicking it
4) look for  network.http.pipelining.maxrequests double click it and set the value to 150
5) if you use proxy then look for network.http.proxy.pipelining and double click it and set it to TRUE. 



Raj, all I am abhi_nav from #ubuntu.
As you know, there already exista entry one for nglayout.initialpaint.delay
and one for content.notify.interval                .

But one more thing is the suggestion no. 2. to 5 are ALSO already exists there and have the appropriate value. 
e.g. network.http.pipilining = true already,
maxrequests=8 but when i change it to 150 and restart firefox it is again 8 only.
:( :( :(

pls help me .

---

### Post by Enigmapond on 2010-03-06
Wow...this really does work! Thanks for bumping this thread up and thanks to the OP!!

---

### Post by Rey117 on 2010-03-06
Wow I am amazed...due to the fact that my dorm Internet is friggin' slow...this really sped up my Firefox!!! Kudos!!

---

### Post by Abhijit Navale on 2010-03-06
:confused::confused::confused::confused::confused::confused:

---

### Post by wojox on 2010-03-06
[Firefox optimization and troubleshooting thread]("http://ubuntuforums.org/showthread.php?t=1193567")

---

### Post by Pauligrinder on 2010-03-06
Thanks a lot, I got a massive speedup with my slowmotion'ish 3G connection :)

---

### Post by zellfaze on 2010-03-06
Just to throw this out there.  Setting pipelining to 150 is rather useless.  Firefox only supports pipelining up to 16 (I  believe).  No bad effects from setting it higher, but truth be known, you don't get any higher speeds after 16.

---

### Post by linuxgeek77 on 2010-03-07
> **Abhijit Navale said:**
> Raj, all I am abhi_nav from #ubuntu.
As you know, there already exista entry one for nglayout.initialpaint.delay
and one for content.notify.interval                .

But one more thing is the suggestion no. 2. to 5 are ALSO already exists there and have the appropriate value. 
e.g. network.http.pipilining = true already,
maxrequests=8 but when i change it to 150 and restart firefox it is again 8 only.
:( :( :(

pls help me .


dont worry about the second entry it wont conflict as it is an initer not a string. i was surprised you had it there in teh first place. because firefox by default doesnt have that. dont worry about it. but if you are scared you can. reinstall firefox and try it again from the beginning.

---

### Post by linuxgeek77 on 2010-03-07
> **Rey117 said:**
> Wow I am amazed...due to the fact that my dorm Internet is friggin' slow...this really sped up my Firefox!!! Kudos!!
  your welcomed

---

### Post by linuxgeek77 on 2010-03-07
> **Abhijit Navale said:**
> :confused::confused::confused::confused::confused::confused:

read my reply. :) on your other post.

---

### Post by linuxgeek77 on 2010-03-07
> **zellfaze said:**
> Just to throw this out there.  Setting pipelining to 150 is rather useless.  Firefox only supports pipelining up to 16 (I  believe).  No bad effects from setting it higher, but truth be known, you don't get any higher speeds after 16.
thank you i didnt know that. but. to be setting it to 16 is much slower than 150. in my personal experience. i dont know why

---

### Post by imjafo on 2010-03-07
Hey, thanks for the tip. I just did it on XP and Ubuntu 9.10. What a huge difference. Again, many thanks.

---

### Post by linuxgeek77 on 2010-03-07
> **imjafo said:**
> Hey, thanks for the tip. I just did it on XP and Ubuntu 9.10. What a huge difference. Again, many thanks.

  I am glad it worked for you :).

---

### Post by Jose Catre-Vandis on 2010-03-07
It does seem to be faster :)

---

