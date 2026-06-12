---
title: "help with pam-pgsql and pam-auth-update setup"
date: 2012-08-30
forum: Networking &amp; Wireless
---

### Post by octaneonyx on 2012-08-30
Dear All,

I am trying to set up an Ubuntu 10.04 LTS machine to authenticate using pam-pgsql. The basic idea is to store user details in a PostgreSQL database and let PAM access those data. Could not find any good tutorials after hours of googling, my only information source is the README file provided with libpam-pgsql V0.7.4 which is kind of terse and confusing. In particular it is completely unclear to me whether I can/shall use pam-auth-update or I must mess with the individual /etc/pam.d/XX files (which ones?).

 I set up PAM/LDAP integration previously, for that there are very good tutorials available, and pam-auth-update helps a lot.

My request: if any of you reading this post has actually succeeded in setting up PAM/PgSQL authentication (preferably with pam-auth-update) and has a detailed step-by-step instruction list to follow, then I would very much appreciate reading it. Also, any pointers to a usable Howto would be very much appreciated.

I would also kindly ask you NOT to tell me any of the following:

1) "We cannot answer your question unless you provide us with config files X, Y, Z." My problem here is that I do not even know where to start, no idea which config files to modify. I can tell you, however, that the user DB is running on a separate server with Postgres 9.1, and the client is Ubuntu 10.04 LTS.

2) "You should use $other_technology instead of PAM and Postgres." I have my own good reasons to set up this particular combination.

3) My question is not about authenticating Postgres DB users using PAM, but authenticating Ubuntu users via PAM using Postgres as the user data supplier backend.

I promise to publish a detailed Howto on this forum if I can get this working, but I need your help to start. Many thanks in advance!

---

### Post by octaneonyx on 2012-09-04
No replies so far from the community. However, I can answer my own question now ;)

I found this tutorial: [http://linux.efrei.fr/tutoriaux/pam-nss-pgsql](http://linux.efrei.fr/tutoriaux/pam-nss-pgsql) . It is in French but the config files etc. are commented in English. The main trick is to use libnss-pgsql2, the rest is also nicely described and worked well, except that in the file /etc/nss-pgsql.conf empty lines were causing parsing errors.

---

