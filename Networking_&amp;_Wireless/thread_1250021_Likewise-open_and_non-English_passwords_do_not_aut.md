---
title: "Likewise-open and non-English passwords do not authenticate users"
date: 2009-08-26
forum: Networking &amp; Wireless
---

### Post by .kkursor on 2009-08-26
Hello all!
I have a trouble, maybe somebody encountered it too.
We have an Active Directory domain served by Win 2003 Server based servers. I am from Russia and all usernames and passwords in our network are in Russian.
We are developing Ubuntu-based distribution to replace counterfeit Windowses on some computers. I have a task to join the computers to AD domain. They join perfectly and I am able to login as a domain user.
But there is a problem with language or password encryption, I think. Here are possible combinations of user name and password combinations:
- english login and english password - login successful
- russian login and english password - login successful
- english login and russian password - login fails
- russian login and russian password (the most common case in our network) - login fails

Ubuntu package version:
```
user@admin:~$ dpkg -l | grep likewise
ii  likewise-open                              4.1.2982-0ubuntu2                        Authentication services for Active Directory
```

Did somebody encounter the same problem and is there a solution?
Thank you very much and looking forward for answer.

---

