---
title: "Ubuntu Desktop Guide refers to Gnome 3 no Unity"
date: 2011-04-24
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by vaskark on 2011-04-24
I was just glancing through the Ubuntu Desktop Guide in Natty and have noticed that some of the instructions refer to the Gnome3 interface and not Unity. For example, in Tips & Tricks > Enter Special Characters:

Define a compose key:

1. Click your name in the top bar and select System Settings.
2. Click Region and Language.
etc

Won't this cause a lot of potential confusion for users who refer to this guide, since Natty will not be including Gnome3 as the default interface?

P.S. I think the guide looks really good. I like the new formatting.

---

### Post by cariboo on 2011-04-24
I hope you created a bug report about the problem.

---

### Post by Dawei87 on 2011-04-25
Do you have a link to the instructions? I'm not sure where the problem is. In Natty you can access the system settings by clicking on your name on the top right in the panel.

---

### Post by VMC on 2011-04-25
I'm missing the reference to Gnome3 also. Here's the section in question:

> Compose key
A compose key is a special key that allows you to press multiple keys in a row to get a special character. For example, to type the accented letter é, you can press compose then ' then e.
Keyboards don't have specific compose keys. Instead, you can define one of the existing keys on your keyboard as a compose key.
Define a compose key
Click your name in the top bar and select System Settings.
Click Region and Language.
Select the Layouts tab and click Options.
Find the group called Compose key position. Select the key or keys you would like to behave as a compose key. You can choose keys like Caps Lock, either of the Alt keys, or the menu key. Any keys you select will then only work as a compose key, and will no longer work for their original purpose.


---

### Post by vaskark on 2011-04-25
> **Dawei87 said:**
> Do you have a link to the instructions? I'm not sure where the problem is. In Natty you can access the system settings by clicking on your name on the top right in the panel.
Go to the dash and open Help to open the Ubuntu Desktop Guide
Click *Tips & tricks*.
Click *Enter special characters*.
Go to the *Compose key* section.

When I click my name in the top panel I do not have a System Settings option; that's under the Logout button for me. And in System Settings there is no Region and Language options -- I have to open Keyboard then the Layouts tab, then Options.

Does this help? Hopefully I've explained better ;)

---

### Post by vaskark on 2011-04-25
> **cariboo907 said:**
> I hope you created a bug report about the problem.
Kinda embarrased to admit this, but I've never done that before :( Can you point me in the right direction?

---

### Post by r-senior on 2011-04-25
Once you have a Launchpad account, it's very easy. You can either file a bug direct in the web site or, if you know which package it is, you can run 

```
ubuntu-bug <package>
```

and it will collect relevant information about your system, search for existing bugs and then walk you through creating a new one.

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

In this case, it's already reported but why not create your Launchpad account and add yourself to the "affects me":

[https://bugs.launchpad.net/ubuntu/+source/yelp/+bug/768223](https://bugs.launchpad.net/ubuntu/+source/yelp/+bug/768223)

---

### Post by vaskark on 2011-04-25
> **r-senior said:**
> Once you have a Launchpad account, it's very easy. You can either file a bug direct in the web site or, if you know which package it is, you can run 

```
ubuntu-bug <package>
```and it will collect relevant information about your system, search for existing bugs and then walk you through creating a new one.

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

In this case, it's already reported but why not create your Launchpad account and add yourself to the "affects me":

[https://bugs.launchpad.net/ubuntu/+source/yelp/+bug/768223](https://bugs.launchpad.net/ubuntu/+source/yelp/+bug/768223)
Great! Thanks.

---

### Post by terry_gardener on 2011-04-25
i asked question like this on askubuntu.

check out 

[http://askubuntu.com/questions/35470/desktop-guide-for-11-04-provides-incorrect-information]("http://askubuntu.com/questions/35470/desktop-guide-for-11-04-provides-incorrect-information")

---

### Post by jbicha on 2011-04-25
Yes, this [bug]("http://pad.lv/753072") has already been reported. And the particular part about the Special Characters page was fixed recently and will be in the next Help update later this week. I don't think that part will be fixed on the install CD but it will be fixed as soon as the computer is updated after install.

If you'd like to help us improve the Help, consider joining me on the [Ubuntu Documentation Team]("https://launchpad.net/%7Eubuntu-doc-contributors").

---

### Post by vaskark on 2011-04-25
> **jbicha said:**
> Yes, this [bug]("http://pad.lv/753072") has already been reported. And the particular part about the Special Characters page was fixed recently and will be in the next Help update later this week. I don't think that part will be fixed on the install CD but it will be fixed as soon as the computer is updated after install.

If you'd like to help us improve the Help, consider joining me on the [Ubuntu Documentation Team]("https://launchpad.net/%7Eubuntu-doc-contributors").
I shall do that. I'd love to help in any way that I can :)

---

