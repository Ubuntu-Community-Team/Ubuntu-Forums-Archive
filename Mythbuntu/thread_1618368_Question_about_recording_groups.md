---
title: "Question about recording groups"
date: 2010-11-10
forum: Mythbuntu
---

### Post by bance on 2010-11-10
I understand that recording groups are a useful way of managing recordings, what I'd like to know is if there is a way to nest them? E.G. 


comedy
             >classic comedy
             >sit-com
             >stand-up


Also is it possible to automatically assign a recording group to a particular machine? So that all recordings made by machine A are stored in storage group A.

TIA Steve,

---

### Post by tgm4883 on 2010-11-10
Recording groups are local, so you won't have one machine record to another machine's hard disk

---

### Post by bance on 2010-11-10
Thanks for the reply,

I'm sorry perhaps I wasn't clear, I'm using various front-ends, and as far as I know all recordings are stored on the back-end.

 What I'm trying to achieve is that each front-ends recordings go into one group that is further devided by genre, sub-genre etc.

 This would mean that one wouldn't have to trawl through all recorded material, in order to find what was required.

Or are you telling me that "Recording Groups" is simply a way of displaying recordings that have been given a certain classification, 

rather than a directory type structure that contains the recordings?

Thanks once again, Steve

---

### Post by tgm4883 on 2010-11-10
> **bance said:**
> Thanks for the reply,

I'm sorry perhaps I wasn't clear, I'm using various front-ends, and as far as I know all recordings are stored on the back-end.

 What I'm trying to achieve is that each front-ends recordings go into one group that is further devided by genre, sub-genre etc.

 This would mean that one wouldn't have to trawl through all recorded material, in order to find what was required.

Or are you telling me that "Recording Groups" is simply a way of displaying recordings that have been given a certain classification, 

rather than a directory type structure that contains the recordings?

Thanks once again, Steve

I was strictly answering your second question. A frontend cannot record at all, so you have secondary backends on there as well. Those backends will not record to a master backend without some additional setup (like NFS shares)

---

