---
title: "git push heroku master fails (firewall &amp; proxy settings issue)"
date: 2011-11-29
forum: Networking &amp; Wireless
---

### Post by Lavix on 2011-11-29
I set up the proxy during the installation of Ubuntu 10.04 via VirtualBox on a Windows XP PC. Installation of ruby, rails and gems was ok.
Then I set up user and password for git global config.
Set up proxy as well:
```

a187589@ubuntu:~$ git config --get http.proxy
http://mycompany.net.:3128

```
Nevertheless, when try to push to Heroku:
```

a187589@ubuntu:~/rails_projects/auchan_pl_specs$ git push heroku master

```
I get a time out error:
```

ssh: connect to host heroku.com port 22: Connection timed out
fatal: The remote end hung up unexpectedly

```
the same result if I try to clone an existing repo fro git:
```

a187589@ubuntu:~$ git clone git@heroku.com:front-tests.git -o heroku
Initialized empty Git repository in /home/a187589/front-tests/.git/
ssh: connect to host heroku.com port 22: Connection timed out
fatal: The remote end hung up unexpectedly

```
Does anyone have an idea?
Thanks.

---

