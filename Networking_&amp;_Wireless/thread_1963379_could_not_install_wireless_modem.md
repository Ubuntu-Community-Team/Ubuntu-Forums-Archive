---
title: "could not install wireless modem"
date: 2012-04-22
forum: Networking &amp; Wireless
---

### Post by zihanls on 2012-04-22
I got problem while installing my wireless modem. I'm from bangladesh. My internet provider is "[banglalion]("http://www.banglalionwimax.com/")"
How can i install my wimax modem?

---

### Post by dandnsmith on 2012-04-22
Start by supplying more info:
*sudo lshw -C network*
*sudo lspci -v*

and give the version of Ubuntu (?) you're using.

With this posted, we might be able to make a start on advising you.

---

### Post by zihanls on 2012-04-23
I use the latest version of Ubuntu. That is Ubuntu 11.10

---

### Post by dandnsmith on 2012-04-23
And the rest?

---

### Post by zihanls on 2012-04-23
I dont know about "sudo lshw -C network", "sudo lspci -v".
Where i can find those info?

---

### Post by dandnsmith on 2012-04-23
Do you know how to call up a Terminal from the Applications Menus, and then enter commands?

---

### Post by zihanls on 2012-04-23
No, I dnt know. Please tell me details.

---

### Post by dandnsmith on 2012-04-23
On the left of the screen is a vertical bar with icons.
As you hover the mouse over each it will give you a name - you want **Terminal**
If it isn't there then go to the Dash (top icon) and enter **term** in the search bar - a set of possibles will appear, with Terminal amongst them.

BTW you should probably have started in the beginners forum, needing answers to such basic questions.

---

### Post by westie457 on 2012-04-23
The use of sudo on the commands that 'dandnsmith' gave you is not really necessary. the output will be the same. Usind 'sudo' will require your password (the one you created when installing Ubuntu), nothing will show on the screen as you type the password.

When you have run those commands copy the output (one way is press Ctrl+Shift+C), come back here and click on 'New Reply' then click the # symbol at the top of the message pane and paste into the [ code][ /code] brackets that appear. This will make it easier for us to read.

Hope this helps.


PS: Welcome to the Forums.

---

### Post by dandnsmith on 2012-04-23
> **westie457 said:**
> The use of sudo on the commands that 'dandnsmith' gave you is not really necessary. the output will be the same. Usind 'sudo' will require your password (the one you created when installing Ubuntu), nothing will show on the screen as you type the password.


Without the 'sudo' for these you don't get all the information, and for some commands you don't get anything at all

---

### Post by westie457 on 2012-04-23
> **dandnsmith said:**
> Without the 'sudo' for these you don't get all the information, and for some commands you don't get anything at all

Okay so not all information is supplied without 'sudo' however there is enough to identify the equipment in use.

Having said that I was trying to explain something to the OP to save him/her the frustration of not being able to obtain and post the information that you have requested.

There is no point in us arguing about this. Shall we get on with the idea behind the Forum which is to help and advise others.

If this has upset you then I apologise.

---

### Post by dandnsmith on 2012-04-23
I wasn't really upset, just remembering one thread which proved to be very protracted because parameters to a command weren't used as given.

I agree that here the vital information will be supplied - the sooner the better for problem resolution.

---

