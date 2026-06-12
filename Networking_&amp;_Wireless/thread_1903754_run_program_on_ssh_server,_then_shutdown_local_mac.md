---
title: "run program on ssh server, then shutdown local machine - problem"
date: 2012-01-03
forum: Networking &amp; Wireless
---

### Post by Unkraut on 2012-01-03
Hello!
I want to do the following:
Log on to an ssh server where I run a program that takes a looong time to finish. In the meantime it might happen that I want to shut down my local computer. When I then login to ssh later I see that the program I started was terminated before it finished.
How can I have a program running on the remote server via ssh without being logged in all the time?
Regards
Unkraut

Edit: Sorry, I already found a good answer here: [http://stackoverflow.com/questions/954302/how-to-make-a-programme-continue-to-run-after-log-out-from-ssh](http://stackoverflow.com/questions/954302/how-to-make-a-programme-continue-to-run-after-log-out-from-ssh)

---

### Post by Lampi on 2012-01-03
use screen, start script, then detach window and logout :)

mark thread as solved if you have a solution

---

