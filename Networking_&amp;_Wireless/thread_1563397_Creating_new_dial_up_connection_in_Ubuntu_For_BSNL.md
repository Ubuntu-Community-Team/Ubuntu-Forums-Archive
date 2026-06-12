---
title: "Creating new dial up connection in Ubuntu For BSNL broadbnad"
date: 2010-08-29
forum: Networking &amp; Wireless
---

### Post by gaurav sontakke on 2010-08-29
Hi All
   I am using Ubuntu 9.10 . And Using BSNL broadband I want to know that how to create new connection using username and password as we do it in windows.

       I have used pppconfig command but it gives me error that no dialer found 

        Whats the issue please help me out.

and tell me how to create dialer in Ubuntu 9.10



Thanking You
gaurav sontakke

---

### Post by dineshs on 2010-08-29
Please follow [this]("http://ubuntuforums.org/showpost.php?p=9611450&postcount=2")
By the way I have a suggestion.You need dialler since your modem is in bridge mode.You can configure your modem in PPPoE mode so that the connection will be always ON.Configuring different modems in PPPoE mode is explained [here]("http://ernakulam.sancharnet.in/ernakulam/bbservice.html")(under modem/CPE config)

---

### Post by varunendra on 2010-08-30
> **dineshs said:**
> Please follow [this]("http://ubuntuforums.org/showpost.php?p=9611450&postcount=2")
By the way I have a suggestion.You need dialler since your modem is in bridge mode.You can configure your modem in PPPoE mode so that the connection will be always ON.Configuring different modems in PPPoE mode is explained [here]("http://ernakulam.sancharnet.in/ernakulam/bbservice.html")(under modem/CPE config)

+1
However, you should check whether it suits your connection plan. It (PPPoE mode in modem) is recommended mostly for 'unlimited' plans.

---

### Post by dineshs on 2010-08-30
> **varunendra said:**
> +1
However, you should check whether it suits your connection plan. It (PPPoE mode in modem) is recommended mostly for 'unlimited' plans.
Can you explain why is it so?

---

### Post by varunendra on 2010-08-30
> **dineshs said:**
> Can you explain why is it so?

Just in case he has a really small "free download" limit that he comes close to, and his computer/(s) download/(s) large volume updates in the background inflicting extra billing on him.

I have experienced it once. We had a 1GB limit on 256Kbps connection, and without knowing it, we ended up downloading almost 5GB only in mails & updates (okay,.. I was 'new' to internet then,.. didn't know how to moniter bandwidth/conn. usage.. ;))

So even if he knows his limit is quite small (if it is) and stays careful, there maybe occasions when he forgets to switch off the modem and computer/(s) end up downloading something large in volume surpassing the "limit".

Not a big issue these days, I know, but for some it maybe....

Do I sound like.... well.. you know what.. :D

---

### Post by dineshs on 2010-08-30
You are right.I have heard of heavy downloads caused by viruses(in Windows).As far as linux is concerned it will not be a problem.Your point is correct

---

### Post by varunendra on 2010-08-30
> **dineshs said:**
> You are right.I have heard of heavy downloads caused by viruses(in Windows).As far as linux is concerned it will not be a problem.Your point is correct

Thank God I'm safe.... (sigh)! I started looking for cover! :lol:

---

### Post by raghavdeepak on 2010-08-30
He can always power off his modem, when not in use!!! Thats what i do....

---

### Post by varunendra on 2010-08-30
> **raghavdeepak said:**
> He can always power off his modem, when not in use!!! Thats what i do....Welcome to the spicy discussion!

Since I've used that mode with a limited plan in the past (still using with 'unlimited' one), I know this as a common practice.

But don't you agree that there is something we call "Human Mistake"?
> **varunendra said:**
> So even if he knows his limit is quite small  (if it is) and stays careful, **[COLOR=Red]there maybe occasions when he forgets to  switch off the modem[/COLOR]** and computer/(s) end up downloading something large  in volume surpassing the "limit".

So it was just an advice to confirm his plan assuming it maybe a small one and he maybe absolutely new to PPPoE like I was once!

---

### Post by raghavdeepak on 2010-08-30
Yeah, I do agree. But if you can make it a practice and if you are already a victim of excess billing caused due to the above (As I was). I dont think you will ever forget to switch it off.....:)

One Q :- Is there any practical difference in speed in both modes?

---

### Post by varunendra on 2010-08-30
> **raghavdeepak said:**
> But if you can make it a practice and if you are already a victim of excess billing caused due to the above (As I was). I dont think you will ever forget to switch it off.....:)
So let's let people learn from mistakes.... :lol:

> **raghavdeepak said:**
> One Q :- Is there any practical difference in speed in both modes?
In terms of speed- No!
Otherwise, PPPoE in modem is easier & stable. In OS, it is prone to errors caused by system changes. So if I focus on that aspect only, I'd advise PPPoE in Modem.

Now let's wait for Gaurav to hear what's he going with.

---

### Post by raghavdeepak on 2010-08-30
Thanks for the answer!

---

### Post by gaurav sontakke on 2010-09-02
Really Thank you for the discussion ,, and answers ..
:D

---

### Post by varunendra on 2010-09-02
If you got your problem solved, please consider mentioning how you got it, and marking this thread as [Solved]. (If there' still some difficulty, please ask)

It helps others browsing for help with same problem.

Thanks

---

