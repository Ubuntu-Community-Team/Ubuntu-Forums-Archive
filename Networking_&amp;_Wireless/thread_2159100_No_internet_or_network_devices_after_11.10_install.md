---
title: "No internet or network devices after 11.10 install from LiveUSB"
date: 2013-07-01
forum: Networking &amp; Wireless
---

### Post by seacher1 on 2013-07-01
Hello All,

I have no wired or wireless connection after an install from a LiveUSB.

I have tried every post that I can find for two days now to no avail.

Has anyone had any success on troubleshooting this issue or can direct me to a webpage that can help?

Thanks for the help.

---

### Post by newbie-user on 2013-07-02
In the terminal, type:
```
lshw -class network
```
to see what kinds of network adapters you have. That will get you started on troubleshooting.

---

### Post by varunendra on 2013-07-03
seacher1,

Why are you even bothering with 11.10? It has reached its "End Of Life", means it is no longer supported : [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

I'd suggest you install the latest LTS instead, that is, 12.04, and maybe both your network interfaces would work out-of-box. If not, troubleshooting it there would make much more sense as it will be supported till April 2017.

If you install 12.04 (or any supported version), and still have problem, I'd suggest to either edit your first post and thread title, or start a new thread with relevant title as the current one will no more be relevant.

---

### Post by seacher1 on 2013-07-03
I realized this after I posted.

I installed three different versions until I found one where the internet worked (13.04).

Then I read the posts again.

Thanks for the help again guys.

---

### Post by varunendra on 2013-07-03
> **seacher1 said:**
> I installed three different versions until I found one where the internet worked (13.04).

Glad it did :)

You may wish to upgrade to 14.04 when it comes out in April next year, as 13.04 will be supported till January only (it'll keep working afterwards, but you won't get updates for it). Alternatively, you can install 12.04 now, then install the backported driver/kernel on it to get the latest drivers available in 13.04 :)

As you've got it working, please consider marking the thread as [Solved] now if you are satisfied with the solution.

---

