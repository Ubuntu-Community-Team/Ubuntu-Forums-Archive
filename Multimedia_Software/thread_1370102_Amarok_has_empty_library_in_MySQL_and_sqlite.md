---
title: "Amarok has empty library in MySQL and sqlite"
date: 2010-01-01
forum: Multimedia Software
---

### Post by thedaylights on 2010-01-01
Recently I reinstalled Amarok 1.4 with mysql support. I had installed it previously and set up a mysql server but I did not compile from source and enable mysql support. So I was having the problem that my library would rebuild each time I loaded Amarok.

When I reinstalled Amarok 1.4 I compiled from source and enabled mysql. However the library does not build at all now. When I choose "rebuild library" nothing happens.

Then I tried sudo apt-get purge remove amarok to get rid of the configuration files. I uninstalled mysql. Then I reinstalled both. Still no library building. I tried uninstalling both, then searching for configuration files for amarok and mysql and deleting them. I found a bunch and deleted them. This time when I reinstalled I got a first time setup wizard for amarok. But still no library building.

I have also tried setting the database to sqlite in Amarok but the library does not build.

I am running Ubuntu 9.10. Please can someone give me some advice?

---

