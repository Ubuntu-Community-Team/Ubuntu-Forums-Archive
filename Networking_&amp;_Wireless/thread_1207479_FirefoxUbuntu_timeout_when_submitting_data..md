---
title: "Firefox/Ubuntu timeout when submitting data."
date: 2009-07-08
forum: Networking &amp; Wireless
---

### Post by Saturisation on 2009-07-08
Hello,

I have encountered some strange behaviour in Firefox. This problem does not occurs arbitrarily, but when it does it can wreak havoc.

Sometimes when i try to submit a form, Firefox halts with the message "waiting for website". After exactly 5 minutes the page goes blank. (http keep-alive setting is set on 300 seconds, so that could be it).

Strangely enough, when a site fails to respond in time, you would get a nice message that the page could not be loaded, instead, all i get is a blank page.

Ajax-posts fail too, and return absolute nothing (no response-headers, no reponse data).

I think the browser is not sending the data, because i have checked the access-logs on my website. This usually occurs when i'm working on a form for a few minutes). If i submit a form within seconds, it wont timeout (strangely enough).

How can i diagnose/solve this problem?

Thanks in advance!

PS. Had trouble submitting this message too, after i click submit, Firefox waits and does nothing. The post has not been added.

I've searched the internet for a solution, could not find any. To be more specific about the problem.

When this problem occurs, Firefox states (in the status-bar): Connecting to website (ok), than hangs on "waiting for website". After waiting for 5 minutes or so, it displays a blank page, not a timeout-message as you would expect. If you re-submit the data (by pressing F5), the problem remains. if you reload without resubmitting, the page loads normally...

It happens in Ubuntu 8.04, Ubuntu 9.04, Firefox 3.0.1 and Firefox 3.5.1pre, but never on a Windows machine with Firefox. (all Same network)..

---

### Post by kirilisa on 2010-03-14
Did you ever sort this out? I'm having the same problem...

---

### Post by saedz on 2011-04-25
same problem here, I have also upgraded the ADSL router's firmware,but the problem is still there
 
my post: [http://ubuntuforums.org/showthread.php?t=1729634](http://ubuntuforums.org/showthread.php?t=1729634)

---

### Post by jean.deruelle on 2011-11-10
I have the same issue, did you find any fix or submitted an issue somewhere ?

Thanks in advance
BR

---

