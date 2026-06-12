---
title: "QQ video with Empathy?"
date: 2010-07-24
forum: Multimedia Software
---

### Post by Robbyx on 2010-07-24
I seem to have successfully logged into QQ via empathy but there is no video or sound. The help file is not clear because it suggests it is possible to have sound and video on both google talk and QQ, if I have the correct plugins. 

What should I do to enable sound and video in  QQ and Talk?

---

### Post by Robbyx on 2010-07-24
Does anyone have an answer my question about video and Empathy?

---

### Post by YannBuntu on 2010-07-27
Hi
I don't know for QQ, but for Gtalk (and Jabber) yes video+audio work perfectly.

To do video+audio chat with Gtalk protocol on Empathy, you need 2 things :
- install the ubuntu-restricted-extras package 
- I also recommend you add ppa:telepathy/ppa to your software sources and update empathy. This should give you the latest version of Empathy (currently 2.30.2)

If your interlocutor uses Windows, he must have a Gmail account and instal the Gtalk plugin in his browser.

If your interlocutors are all on linux, you can do video+audio chat with 3 or more of them with Muji (still in developpment).

---

### Post by Robbyx on 2010-07-27
Thanks for your help. Do you know of a way to test if gtalk is working in empathy? Is there a test site as there is for skype?

---

### Post by YannBuntu on 2010-07-27
You can test video+audio with the testers listed here : [http://forum.ubuntu-fr.org/viewtopic.php?pid=3504884#p3504884](http://forum.ubuntu-fr.org/viewtopic.php?pid=3504884#p3504884)

Just add their Jabber adress in Empathy, and ask them to do a quick test when you see them online :)

(Gtalk is in fact Jabber protocol but passing threw Google servers, so it is compatible with Jabber)

---

### Post by Robbyx on 2010-07-28
As it is in French could you give me the test address from the posting you sent me?

Will Jabber/ gtalk video and sound take up less bandwidth than skype? That is why I am trying to make the change from skype.

---

### Post by YannBuntu on 2010-07-28
> **Robbyx said:**
> As it is in French could you give me the test address from the posting you sent me?

it is not a test address. They are volunteers (humans, like you and me), who propose to test video+audio with them.
Just add the Jabber adresses that are noted [English ok] in your Empathy contacts.

> **Robbyx said:**
> Will Jabber/ gtalk video and sound take up less bandwidth than skype? That is why I am trying to make the change from skype.

Concerning Empathy I don't know. With Ekiga you can select the video codec you want, so maybe you can decrease the bandwidth.

---

