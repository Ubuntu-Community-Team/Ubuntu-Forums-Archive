---
title: "Deja Dup &quot;Giving up after 5 attempts. ApiRequestError: None&quot;"
date: 2022-06-24
forum: Multimedia Software
---

### Post by advancedtribute on 2022-06-24
*Ubuntu 20.04, HP Envy Laptop.*
Per title, when I try to backup my /home folder, the backup tool seems to do all of this hard work to backup my Directory into Google Drive.

However, right when it gets to the end of the process, Deja Dup fails and gives me an error stated as, [I]"Giving up after 5 attempts. ApiRequestError: None".

[/I]I have made sure to clear some space so that there is room for my backup data inside of Google Drive, but this did not help.

My backup used to work, but since then I have made some automatic updates that come straight from Ubuntu. Other than that, I have not altered my OS in any particularly major way, so I don't think that this should be a problem.

Does anybody know the steps I can take to overcome this problem? Is there a better tool I can use instead? I would rather backup to a Google drive but at this rate I may need to buy some USB storage and copy all of the contents via offline means before I eventually store more data and move to 22.04.1 when it releases...

This is my first post to this forum and I am hoping that I provided you all the details necessary in order to help me work on this problem. Thank you for your time! :KS

---

### Post by TheFu on 2022-06-24
I avoid google and don't use Deja Dup,  but didn't Google recently change to mandating OAuth2 be used for authentication?  I know they did on gmail, so I haven't checked any gmail since that change.

A web-search for similar issues found a number of bugs beginning in 2018, so it may not be Oauth2 that is the problem.
Try running the tool from a shell (not through a menu) so all the info, warning, and error messages can be seen in the terminal to provide more clues to the root issue.

---

### Post by advancedtribute on 2022-06-30
Heya, thanks for the response! I actually read your reply earlier but didn't come around to responding to it.

I solved my issue by simply using a different G-drive account. (hehe!)

The problem was my previous account was apparently full, and even after clearing all of my largest files it still reads "99%" full. Backing up with Deja-Dup was always working (in my experience) but Google was the one causing me problems here. I still do not trust it so I will refer to an offline storage medium instead.

I originally wrote this post thinking that the error returned by Deja-Dup meant it wasn't able to even begin uploading files. But digging around showed me this was not the case.

---

### Post by TheFu on 2022-06-30
Why not tell everyone that you've solved it?

Thread Tools button ---> SOLVED.  This helps people seeking answers and stops people like me from wasting more time for an already solved issue.

Please and thank you.

---

