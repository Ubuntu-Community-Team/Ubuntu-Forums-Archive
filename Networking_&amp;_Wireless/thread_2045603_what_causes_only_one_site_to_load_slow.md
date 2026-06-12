---
title: "what causes only one site to load slow?"
date: 2012-08-21
forum: Networking &amp; Wireless
---

### Post by Sylos on 2012-08-21
This isnt an ubuntu specific problem. It affects windows too.

Im part of a forum (its closed membership so I cant offer it up to be tested) and many of the users are complaining about the amount of time it takes to load threads with multiple responses. Im not the admin - just a user snooping into what could be the cause (the admins are doing nothing it seems). 

The main organisation website works as normal - only when you enter the forum area do you get the slow loading. I can ping the IP and get 28ms typical response time.

SO just wondering if anyone has any ideas why this would be happening or what, if anything, I could do to see why it is happening.

Cheers

---

### Post by ajgreeny on 2012-08-21
Is the site flash or image heavy?

In Firefox go to **Tools -> Page Info** or hit Ctrl+I and see what the page contains.

---

### Post by Sylos on 2012-08-22
Thanks for the reply.

There are only little avatar images - no flash or other large content. Thats why it seems so strange that it is very slow loading. And the load time for a thread page gets longer the more posts there are on the page. The main organisation front page has way more pics and content on it but loads like any other normal website.

I can only assume at the moment its something about the way the forum is set up and how the pages are coded. Sadly I know nothing about html so when I did look at the page content it didnt mean much to me.

---

### Post by era86 on 2012-08-22
Well, it could be anything. Slow hosting? Inefficient data loading? Sending HTML chunks over the wire? You can inspect using Firebug or Chrome Debugger to see if it's something over the wire or on the client side (JavaScript code).

Have fun!

---

### Post by Sylos on 2012-08-22
Cheers for the suggestions. The search continues....

---

