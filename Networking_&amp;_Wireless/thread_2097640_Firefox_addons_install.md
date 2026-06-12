---
title: "Firefox addons install"
date: 2012-12-23
forum: Networking &amp; Wireless
---

### Post by Jvdy on 2012-12-23
in windows we can just simple install addons in firefox and all user can use it
but in ubuntu i found if i install addons it only install for the user i logged in 
i.e : if i log on as _'user1'_ open firefox install dta(down them all) addons i can use dta, but if i log on as another user or create a new _'user2'_ _'user2'_ must install dta again to use dta

how can i just install **addons** for _**all user**_ in my ubuntu 12.04.1 system???:confused:

---

### Post by Jvdy on 2012-12-23
anyone here??

---

### Post by sammiev on 2012-12-23
Please give up to 24hrs before you bump your thread. Someone will be buy shortly. :)

---

### Post by vasa1 on 2012-12-24
> **Jvdy said:**
> in windows we can just simple install addons in firefox and all user can use it
but in ubuntu i found if i install addons it only install for the user i logged in 
i.e : if i log on as _'user1'_ open firefox install dta(down them all) addons i can use dta, but if i log on as another user or create a new _'user2'_ _'user2'_ must install dta again to use dta

how can i just install **addons** for _**all user**_ in my ubuntu 12.04.1 system???:confused:
In Ubuntu, users have their own profile(s). 
So, if you look at each user's home folder, you'll see something like this:
/home/user_1/.mozilla/firefox/random.default  
/home/user_2/.mozilla/firefox/random.default  
/home/user_3/.mozilla/firefox/random.default  
and so on.
Note that .mozilla refers to a hidden folder and you'll have to enable viewing of hidden files and folders to see it in a file manager. In Nautilus, I think you use control+H.

While it's possible as admin to copy over the extensions folder, I'm not sure it's a good idea at all because the process of actually installing an extension may require altering other critical files.

BTW, what is your thinking behind your question? Is it to save bandwidth? Unfortunately, keeping the OS and programs updated and secure is going to use quite a bit of bandwidth. I advise you to get an "unlimited" plan, if possible, to avoid the pain.

---

### Post by Jvdy on 2012-12-25
> **vasa1 said:**
> 
BTW, what is your thinking behind your question? Is it to save bandwidth? Unfortunately, keeping the OS and programs updated and secure is going to use quite a bit of bandwidth. I advise you to get an "unlimited" plan, if possible, to avoid the pain.

yes of course  but if i choose unlimited plan its to much expensive for me
thank for advice
i found my downloaded .xpi files and with that i can simply open in nautilus as root and drag it to firefox to install for different user.
its in here 
/home/<username>/.mozilla/firefox/<randomname>.default/extensions/

thanks again

---

