---
title: "Concurrent Writing to an External HD Over Network?"
date: 2010-10-11
forum: Networking &amp; Wireless
---

### Post by csharpplus on 2010-10-11
I have ten laptops, each with a HD of size 60[GB]. I am planning to start using a scientific application that needs (per each instance of it; and I will be running 10 instances _concurrently_-- one per each computer) about 150-200[GB] per each instance.
Just to make it clear, the 150-200[GB] are the output (binary files) of the scientific app.
 
Since my hard drives on the 10 machines are small, I had an idea. Being an Ubuntu newbie, I am not sure if the idea is good. Your thoughts?
 
I thought of taking another computer, call it laptop11, and connect an external hard drive (of size 2[TB]) to it, mounted permanently. then, I would create 10 different directories in this external hard drive, with the following names: {laptop**1**, laptop**2**, laptop**3**, ..., laptop**10**}, each with 200[GB] of free space.
 
I will then mount folder 'laptop**1**' of the external hard drive to a local folder on machine 'laptop**1**'. mount folder 'laptop**2**' of the external hard drive to a local folder on machine 'laptop**2**'. mount folder 'laptop**3**' of the external hard drive to a local folder on 'laptop**3**' and so forth for all machines.
 
This way, I will be able to run all the machines in parallel and overcome the HD limitations of the laptops. let's assume that 'laptop**11**' is idle, and not running any programs (is used solely for the purpose of 'exposing' this external hard drive).
 
The question is, will this work? meaning, will the writing be fast enough, given the fact that 10 machines are writing to the same HD at the same time? (otherwise, I will have a serious bottleneck...). 
 
Can this idea work? If yes, can this idea work with 20 machines as well? If not, can this idea work with 5 machines instead of 10?
 
Any other ideas to solve this problem are welcome (note though that my budget is limited...). thank you.

---

