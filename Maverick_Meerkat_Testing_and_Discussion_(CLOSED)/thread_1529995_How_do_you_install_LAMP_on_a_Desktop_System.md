---
title: "How do you install LAMP on a Desktop System?"
date: 2010-07-13
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by cariboo on 2010-07-13
I was answering some questions in ABT, and I came upon a post where someone wanted to install Apache, Mysql and Php. I wasn't sure what the Synaptic command was. There used to be a menu item under edit called **Install Packages by Task**, it is no longer there, you could also use this command to install packages for Ubuntu Studio, Mythbuntu and Kubuntu  among other tasks. I also searched the Software Center for an option to install the LAMP stack. Even tasksel isn't installed by default on my  June 9th daily build based install.

Not everybody wants to install server packages on their desktop system, but there are quite a few people who do for testing, educational or even work related reasons. Is it worth creating a bug about this, or should I just ignore it?

---

### Post by _oOMOo_ on 2010-07-13
I guess you just install the packages individually, from memory:

sudo apt-get install apache2 libapache2-mod-php5 php5 mysql-server-5.1 php5-mysql

should do it.

---

### Post by Cenotaph on 2010-07-13
sudo tasksel install lamp-server

that doesn't work anymore? im not testing maverick yet

---

### Post by soapytheclown on 2010-07-13
> **Cenotaph said:**
> sudo tasksel install lamp-server

that doesn't work anymore? im not testing maverick yet

that works fine i ran it the other day ;)

---

### Post by frustphil on 2010-07-13
For me, I'd like to have a LAMP stack readily available in USC. It would greatly help less technical people like me. :-)

---

### Post by cariboo on 2010-07-13
> **Cenotaph said:**
> sudo tasksel install lamp-server

that doesn't work anymore? im not testing maverick yet

That works, but if you read my post, you'll see that tasksel isn't installed by default.

---

### Post by phillw on 2010-07-13
I'd guess tasksel will arrive by default sometime during the cycle, I've not seen any mention of not having it there.

The use of tasksel for LAMP sure makes life a lot easier for me to support, and is the method I've proposed for the server manual. I guess I need to go check and ensure it is still going to be there. Else my 1st command will be sudo apt-get install tasksel :-\

Regards,

Phill.

---

### Post by cariboo on 2010-07-13
I'm sure tasksel will show up in the server install, by default. It's the removal of install packages by task in synaptic that I'm wondering about.

---

### Post by 23meg on 2010-07-13
> **phillw said:**
> I've not seen any mention of not having it there.

Here you go:

[https://launchpad.net/ubuntu/+source/ubuntu-meta/1.199](https://launchpad.net/ubuntu/+source/ubuntu-meta/1.199)

It's only been removed from the minimal [seed]("https://wiki.ubuntu.com/SeedManagement"), though. It's still part of the alternate CD and the server edition (probably pulled in via a dependency; I don't see it explicitly seeded).

---

### Post by 23meg on 2010-07-13
> **cariboo907 said:**
> It's the removal of install packages by task in synaptic that I'm wondering about.

That functionality (I'm assuming you mean "Mark packages by task") uses tasksel, and is only available in Synaptic when tasksel is installed. Try removing tasksel in a stable release and it will disappear from the menu.

---

### Post by cariboo on 2010-07-13
Being literal minded, that looks like they want to remove tasksel from the minimal install. :)

I did install tasksel and the option to mark packages by task came back.

I bugged it anyway.

---

### Post by 23meg on 2010-07-13
> **cariboo907 said:**
> I bugged it anyway.

The issue boils down to whether tasksel should exist on the desktop edition, which, being a discussion of defaults, is [better suited]("https://help.ubuntu.com/community/ReportingBugs#When%20not%20to%20file%20a%20bug") to be taken up in the development mailing lists rather than a bug report.

---

### Post by cariboo on 2010-07-13
I joined the mailing list too.

---

### Post by phillw on 2010-07-14
I've also joined.

It'd be a real shame if tasksel is removed from the desktop for those who want LAMP on their desktop system (or any of the other goodies it gives an easy way to install) instead of people using search engines to get out of date installation instructions.

Regards,

Phill.

---

### Post by AlexanderDGreat on 2010-07-23
Hi cariboo907 - I always use a LAMP server on a desktop because. I'm a freelance PHP developer at the same time, system admin in a small office.

Before I use the sudo apt-get install apache2 libapache2-mod-php5 php5 mysql-server-5.1 php5-mysql

But that's too hard to remember, and it's painful down the road, if you forgot a dependency there (almost all tutorials on Google, has different versions which to install, it's really quite confusing). The painful part, what if a PHP command, etc... didn't work just because you forgot to install a dependency or functionality, you will play detective - if your code is wrong, or the system is wrong.

So I attended a seminar and said it's easier to sudo apt-get install lamp-server^ --- but my main concern for this is, how do you uninstall that friggin' thing?

So again I searched, until now I don't know the answer. Whereas when I was a Windows user, I'd just download WAMP - all easy! And I'm using a desktop.

So now I just use sudo tasksel. Then select LAMP Server - at least this has an UNINSTALL --- just untick the service you don't want to.

I used WAMP for 3 years now, when I changed to Ubuntu, up to now, I don't know what to install for 2 years now!!!

It's painful not to be able to have a simple WAMP in Ubuntu, with all the interface there.

Also, I've been wanting to install PHP 5.3 now, but sudo tasksel, LAMP Server only gives my PHP 5.2! More painful, they said, compile PHP 5.3 from source. If you can understand, that's already too difficult for me.

Bottomline, what's the best practice to install LAMP Server on Ubuntu? How can I install it and uninstall it when I want to using a SIMPLE METHOD! What if I want to upgrade PHP 5.3, where do I go?

That's all the confusion and mess that's running in my head. So thank you for the POST.

I'm using Ubuntu Desktop Lucid Lynx 32-bit.

---

### Post by cariboo on 2010-07-24
To install php-5.3 with out having to compile from sourceyou can use this ppa:

```
ppa:bd808/php5.3
```

Go to System->Administration->Software Sources->Other Software, and click the add button.

---

### Post by AlexanderDGreat on 2010-07-24
Thank you so much! I've been Googling this but NO AVAIL! :)

---

