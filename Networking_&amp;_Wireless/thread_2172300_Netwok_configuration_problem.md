---
title: "Netwok configuration problem"
date: 2013-09-04
forum: Networking &amp; Wireless
---

### Post by brick2 on 2013-09-04
Hi, I m getting a massage upon booting my computer "waiting for netwok configuration" , that would be the first one the other two that follow are "Waiting for up to 60 more seconds for network configuration" and "Booting without network configuration". 

It is important to say that this does not create any technical problems as my network seams to be working just fine, however the boot time in really long it takes about 5 min for this process to compleate, every time I tur my computer on. It would be really nice to to put an end to it.

I have searched for the solution and I have found out that many other people have the same problem but they had a much diffrent cause and their solution well, would not work for me.

There are 2 connection by that I mean 2 diffrent types as in standard cable connection or at least I think it is call so and DSL connection, furthermore they are from 2 diffrent internet providers in two diffrent places. 
If I reinstall ubuntu 12.04 and just use the cable connection this problem does not happen however when I configure the DSL connection with PPPOECONFIG tool this problem appears, I ve managed to figure out that this is simply a GUI problem or that is what people have been saying, there were some sugestions of changing the /etc/network/interfaces.

Contents of /etc/network/interfaces

auto lo
iface lo inet loopback


auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

auto eth0
iface eth0 inet manual


Could anyone help me out with this as I have switched to ubuntu from windows about a year ago so I m still so to say fresh.

Thank you all for your time.

---

### Post by kc-koellein on 2013-09-04
I find it interesting that you run both connections on the same PC and not on a separate router or a separate linux-based router...? 

Did you have this setup working well for you in Windows?

What are you getting from that configuration? ie: what are you hoping to gain by connecting (2) different internet gateways to one PC?

thx
K9SPY

---

### Post by brick2 on 2013-09-09
Ok I have fixed the problem, but thank you for your time anyway, I shall explain what I have done maybe someone else will find it usefull.

This is a copy of an artice I found. It is not a perfect solution but it works.

Okay! That one took me too long!?
 I was searching for "Waiting up to 60 more seconds for [network]("http://linux.m2osw.com/taxonomy/term/169") configuration..." and just couldn't find where the heck that was hidden. It's in /etc/[default]("http://linux.m2osw.com/taxonomy/term/697")/failsafe.conf and if you look at that [file]("http://linux.m2osw.com/taxonomy/term/12") you'll see a few sleep in there.
 I'm not too sure what that's really used for, but having to wait 2 minutes for the [server]("http://linux.m2osw.com/taxonomy/term/193") to [boot]("http://linux.m2osw.com/taxonomy/term/27") seems dramatic when before it used to [start]("http://linux.m2osw.com/taxonomy/term/123") immediately and worked just fine.
 So, [edit]("http://linux.m2osw.com/taxonomy/term/357") the [file]("http://linux.m2osw.com/taxonomy/term/12"), scroll down and remove the sleeps... I do not recommand you do that though, your problem if you break your [system]("http://linux.m2osw.com/taxonomy/term/166"). [IMG]http://linux.m2osw.com/sites/all/modules/ckeditor/ckeditor/plugins/smiley/images/tounge_smile.gif[/IMG]
 The is the [version]("http://linux.m2osw.com/taxonomy/term/137") in Ubuntu 12.04 ([File]("http://linux.m2osw.com/taxonomy/term/12"): /etc/init/failsafe.conf)
     # The point here is to wait for 2 minutes before forcibly booting
    # the [system]("http://linux.m2osw.com/taxonomy/term/166"). Anything that is in an "or" condition with 'started
    # failsafe' in rc-sysinit deserves consideration for mentioning in
    # these messages. currently only [static]("http://linux.m2osw.com/taxonomy/term/723")-[network]("http://linux.m2osw.com/taxonomy/term/169")-up counts for that.

        sleep 20

    # Plymouth errors should not stop the [script]("http://linux.m2osw.com/taxonomy/term/14") because we *must* reach
    # the end of this [script]("http://linux.m2osw.com/taxonomy/term/14") to avoid letting the [system]("http://linux.m2osw.com/taxonomy/term/166") spin forever
    # waiting on it to [start]("http://linux.m2osw.com/taxonomy/term/123").
        $PLYMOUTH message --text="Waiting for [network]("http://linux.m2osw.com/taxonomy/term/169") configuration..." || :
        sleep 40

        $PLYMOUTH message --text="Waiting up to 60 more seconds for [network]("http://linux.m2osw.com/taxonomy/term/169") configuration..." || :
        sleep 59
        $PLYMOUTH message --text="Booting [system]("http://linux.m2osw.com/taxonomy/term/166") [without]("http://linux.m2osw.com/taxonomy/term/628") full [network]("http://linux.m2osw.com/taxonomy/term/169") configuration..." || :

    # give [user]("http://linux.m2osw.com/taxonomy/term/67") 1 second to see this message since plymouth will go
    # away as soon as failsafe starts.
        sleep 1 Be careful, because the $PLYMOUTH calls end with a ||, personally, I commented all those lines and it works with my [server]("http://linux.m2osw.com/taxonomy/term/193") which now boots 2 minutes faster. Imagine that! (Note that what's really important is the [firewall]("http://linux.m2osw.com/taxonomy/term/94"), [MAKE]("http://linux.m2osw.com/taxonomy/term/243") SURE IT'S ON BEFORE THEN!)
 Good luck.

To aswer your question kc-koellein I have two connection set up on my laptop because I keep moving it betweek two flats so it is nececery for me to have them. If you have any other sugestions as to how this may be done I would much appreciate it. 
And yes it works on windows but I do not use it anymore, maybe just to test stuff and for mobile broadband because I can not find drivers for portable huawei modems e303.

I shall mark the post SOLVED in a day or two jsut wona see if anyone has any sugestions as far as the two connections are concerned.

Thank you all for your time.

---

### Post by rooks-netcore on 2013-09-12
umm.. your solutions are very quirky, i found a very simple, surefire method. just edit /etc/network/interfaces and then follow the rest of instructions on my blog,

[http://pleasanthacking.com/2013/09/12/waiting-for-network-configuration-fix-in-ubuntu/](http://pleasanthacking.com/2013/09/12/waiting-for-network-configuration-fix-in-ubuntu/)

It is so easy, just remove one thing. It really is strange that nooone else got it... hope you'll like it :)

---

