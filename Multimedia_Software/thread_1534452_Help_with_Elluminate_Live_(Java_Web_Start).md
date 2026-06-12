---
title: "Help with Elluminate Live (Java Web Start)"
date: 2010-07-19
forum: Multimedia Software
---

### Post by madmercenary on 2010-07-19
Hello,

I am new to Ubuntu, but i cannot seem to get my Elluminate Live to work. When i go to the website it already assumes i do not have Elluminate, so it gives me options of which edition i want (there Ubuntu option only goes upto 8.04). It says further down, that if i am using Linux, than it should already be installed in my system. When i click to join session, it gives me a file dropin.jlnp, and asks what program i want to open it with? This is where i am confused. Any help would be greatly appreciated.

---

### Post by gcordoba on 2012-08-17
For all those who neeed or like to use Elluminate.

There are some issues about sun-java. Elluminate does not work with openjdk, thus we need to install sun-java. 
To do that, follow  [http://www.gaggl.com/2011/10/installing-java6-jdk-on-ubuntu-11-10/](http://www.gaggl.com/2011/10/installing-java6-jdk-on-ubuntu-11-10/) who suggest:

sudo add-apt-repository ppa:ferramroberto/java
sudo apt-get update
sudo apt-get install sun-java6-jdk sun-java6-plugin

However, despite of java being isnatlled, Elluminate still does not work. This is because sun-java-1.6 is blocked by firefox (security issues). Then you need to find where javaws is: 
[http://www.gaggl.com/2011/10/using-blackboard-collaborate-elluminate-on-ubuntu/](http://www.gaggl.com/2011/10/using-blackboard-collaborate-elluminate-on-ubuntu/)

who steted that is better to do:

> sudo update-alternatives --config javaws

In my case the answer to suc a command was:

> sudo update-alternatives --config javaws
[sudo] password for gcordoba: 
There is only one alternative in link group javaws: /usr/lib/jvm/java-6-sun/jre/bin/javaws
Nothing to configure.
 
Then, launch Elluminate. Then, firfox will suggest to use the same mozilla-firefox. Click on Other. Once in the respective window, search for the former path (eg. /usr/lib/jvm/java-6-sun/jre/bin/javaws)

And..done (at least it worked for me)

Note: Following another post I uninstalled Icetea. I do not know if that is actually necessary.

---

