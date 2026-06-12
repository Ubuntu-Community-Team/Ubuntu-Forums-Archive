---
title: "Ok, so what am i doing wrong with mythweb / port forwarding?"
date: 2010-04-18
forum: Mythbuntu
---

### Post by geekyhawkes on 2010-04-18
I am trying to work out what i am doing wrong with port forwarding on my router to get myth web to work.  If i set my myth machine as an exposed host then by entering my ip address I can log in just fine to myth web.  Clearly I dont want to have my myth box as an exposed host on the internet!

I have setup port forwarding on my router for a random port )for this case 3333 will be fine for descussion) to forward to [MYTHBOX IP] address port 80.

When i try and access from outside my home network I get the mythweb login screen fine and enter my user name and password but get no further as I am displayed with ;

HTTP Error 503: The requested service is unavailable.

The service may be unavailable because the server has reached the limit of number of requests it is willing to serve in parallel.  

If i go back and expose the host then all works fine so I am happy mythweb is working ok.  

Do I need to forward more than port80 to get myth web working? 

For what it is worth I am using an orange livebox siemens SE572.

THanks

---

### Post by uncle hammy on 2010-04-18
[http://myhosturl:3333/mythweb](http://myhosturl:3333/mythweb)

You need the /mythweb part if you'r going to use an alternate port.

---

### Post by geekyhawkes on 2010-04-19
Right, why is that?  I am confused why the port forwarding shouldnt just forward all requests to port 80 on the myth box?


By the way, thanks it does work a treat, the question above is more for my understanding of what is going on!

---

### Post by uncle hammy on 2010-04-19
> **geekyhawkes said:**
> Right, why is that?  I am confused why the port forwarding shouldnt just forward all requests to port 80 on the myth box?


By the way, thanks it does work a treat, the question above is more for my understanding of what is going on!
Because mythweb is a secondary site in Apache.  So [http://myapachemachine](http://myapachemachine) doesn't actually go to mythweb, it goes to a default page there that then redirects to mythweb....without the port you specified.  SO by specifically saying "take me to the mythweb site", you don't lose the port as you browse around.

---

### Post by geekyhawkes on 2010-04-20
Thank you, still so much to learn!

---

