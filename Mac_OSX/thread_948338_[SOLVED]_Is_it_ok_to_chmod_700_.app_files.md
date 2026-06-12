---
title: "[SOLVED] Is it ok to chmod 700 .app files?"
date: 2008-10-15
forum: Mac OSX
---

### Post by HungryMan on 2008-10-15
The iMacs I'm currently using are for public use. Now, the owner wants that only certain applications are permitted to run. So, I create a new account, make it the default, go back to the administrator, chmod 700 all the .app files that shouldn't be used in Applications folder (firefox, safari, etc...) and Utilities folder (just terminal). And voila, firefox can not run.

Now, I have 2 questions to ask. First, is this safe? By safe I mean, it wouldn't do any damage to OS X's stability. Second, since there are also PC's with openSUSE there, how can I disable firefox and the like from running only for a certain user?

Thanks in advance!

---

### Post by seanc7 on 2008-10-17
You should be able to do the same thing on Suse that you did in OSX. 

As long as you don't remove permissions to files for root, there should be no issues.

---

### Post by NoSmokingBandit on 2008-10-18
One way to do this is to move the app into the /Users/*username*/Applications folder. I've never done that myself, but im 90% sure that only the user with the app in their folder and thr root user can run the app then.

---

### Post by HungryMan on 2008-10-20
thanks a lot!

---

### Post by Corelogik on 2008-10-22
You can accomplish the same thing front the Parental Controls preference pane. Just create a new user account for public use, open system preferences, go to user accounts, click on the one you want to edit, then click on parental controls.

From their you can set what Apps someone can or can't run and even where they can/can't go on the internet.

---

