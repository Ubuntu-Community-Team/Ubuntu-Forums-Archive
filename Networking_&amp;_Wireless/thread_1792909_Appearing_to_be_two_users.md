---
title: "Appearing to be two users"
date: 2011-06-28
forum: Networking &amp; Wireless
---

### Post by Bre Ntt on 2011-06-28
Hello, 
(I'm not all that clear on TCP/IP and networking and all that, so excuse the ignorance that inevitably permeates the following. )

So I'm wondering how to make it look like you are two seperate users to web-based email clients, social networking sites etc, without, say, switching between sessions in Ubuntu.

I'd like to have, say, two seperate gmail accounts open in Firefox, (without using gmail's clunky double login method). I'd like it to be as if I was on another computer in the house, or working in a different Ubuntu session, only on the same computer, in the same session. (I can switch between sessions in Ubuntu of course, but that is a pretty slow process.)

Is there software to do this? Where I can have two firefox windows open but logged into, say, google with two seperate accounts, so this hould look to google, or whatever site, as if I'm another user on a different computer in the same network. (that wouldn't be the purpose, but would be a side-effect of what I want.)

Thank you, hope I explained myself well.

---

### Post by chili555 on 2011-06-28
> Where I can have two firefox windows open but logged into, say, google with two seperate accounts, so this hould look to google, or whatever site, as if I'm another user on a different computer in the same network.That's exactly the situation with my wife and myself. We both show up on Gmail, obviously, from the same IP address. No one from Google has called or emailed to ask any questions. I suspect this is quite common.

Can't you do it with tabs in Firefox? One logged in as [email]Bre@gmail.com[/email] and the other as [email]Ntt@gmail.com[/email]? I doubt it takes any special software.

---

### Post by Bre Ntt on 2011-06-28
> **chili555 said:**
> 
Can't you do it with tabs in Firefox? One logged in as [email]Bre@gmail.com[/email] and the other as [email]Ntt@gmail.com[/email]? I doubt it takes any special software.

No, if you sign in once, it stays signed into that account, and if you open a new tab or new window, it is still on that account (its a cookie thing, works like this for just about all sites that you log in to, and is a quite convenient feature for most purposes). To go to another account you have to sign out of gmail then sign back in. Gmail has a feature to sign into multiple accounts at the same time, but it's not very well implemented. 

I found a firefox plugin called 'Gmail Manager' that does sort of what I want for gmail, but would like a general solution that would work for other sites as well.

---

### Post by sisco311 on 2011-06-28
You can create multiple profiles in firefox. You can start the profile manager with:
```
firefox -ProfileManager
```

and

```
firefox -P **profile**
```will start firefox with the  profile named **profile**.

---

### Post by Bre Ntt on 2011-06-28
That should work, thanks. 

Edit: They took away the Profile Manager in Firefox 4.0 it appears. But there is a stand-alone profile manager now.

---

