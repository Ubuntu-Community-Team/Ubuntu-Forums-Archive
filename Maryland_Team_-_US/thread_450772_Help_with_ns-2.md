---
title: "Help with ns-2"
date: 2007-05-21
forum: Maryland Team - US
---

### Post by squared on 2007-05-21
I live in southern Maryland.  I'm trying to get ns-2 to run on UBUNTU for my dissertation.  It's been a while since I've used UNIX or C++ and am struggling with it.  I got it to install and verify successfully, but when I type 'ns' it looks like it is pointing to 'host'.  When I type man ns, it seems like it gives me the info for host.  host is not aliased with ns, and I can't figure out what to do short of re-installing it.

---

### Post by Iokua on 2007-05-21
I'm not familiar with ns-2 so I can't help you there, but I recommend that you post this in the help section of the forums. You're much more likely to reach a wider audience and, hopefully, find a solution.

---

### Post by squared on 2007-05-21
Thanks,  I've posted it twice there and got no response.  I'm not sure it's related to ns-2, but that the term 'ns' is somehow interpreted as 'host'.  I get the same response from the terminal when I type either one.  Is there another way that Linux binds user defined terms with system defined commands...like alias, only another way?  I used to be very familiar with VMS and DOS both, but not with Linux.  There has to be a script file that is executing on login/startup that associates ns with host, but I have no clue where to look.

---

### Post by Iokua on 2007-05-22
> **squared said:**
> Thanks,  I've posted it twice there and got no response.  I'm not sure it's related to ns-2, but that the term 'ns' is somehow interpreted as 'host'.  I get the same response from the terminal when I type either one.  Is there another way that Linux binds user defined terms with system defined commands...like alias, only another way?  I used to be very familiar with VMS and DOS both, but not with Linux.  There has to be a script file that is executing on login/startup that associates ns with host, but I have no clue where to look.

I'm not sure I understand exactly what you mean, but are you having trouble executing the program? If so, the current working directory is not generally included in PATH by default, so to execute a program or script, you have to include it, as in:

```
./ns
```

But this will only work if the program you're trying to execute is in your present working directory. If it's somewhere else, you need to include the path to it.

Your problems with the manual may be the result of "ns" (nameserver) being considered a synonym for "host." That may explain why man brings up entries for host. I'm not on my Ubuntu machine right now so I can't test this. If you're looking for documentation specifically for ns-2, I would suggest trying: 

```
apropos ns-2
```

Or you can check the website: [http://www.isi.edu/nsnam/ns/]("http://www.isi.edu/nsnam/ns/")

---

### Post by phegdepatil on 2007-09-22
I have Ubuntu 7.04 Feisty Fawn OS loaded on my laptop and now I have installed ns2.31 (network simulator) using ns2allinone tar file from sourceforge.com, I have followed all the instructions given in it for installation. But when I try to run ns from the prompt it gives NameServer not responding message. kindly help me.

Pratidnya.

---

### Post by aptenix on 2007-09-24
I saw this after a bit of Googling:
[http://www.dii.unimo.it/wiki/index.php/The_Network_Simulator_-_NS_2](http://www.dii.unimo.it/wiki/index.php/The_Network_Simulator_-_NS_2)

---

### Post by Sakthivel on 2008-02-11
Hi ,
  I am doing project in ns2 simulator...
 Actually i have installed ns2 in Windows XP...
 How to make llinkage between C++ ie.,back end and OTCL ie., front end..
How to define protocol in back end ..
Can you give me some examples that uses both C++ and OTCl ...

---

### Post by Ayeshaaltaf on 2008-05-04
> **squared said:**
> I live in southern Maryland.  I'm trying to get ns-2 to run on UBUNTU for my dissertation.  It's been a while since I've used UNIX or C++ and am struggling with it.  I got it to install and verify successfully, but when I type 'ns' it looks like it is pointing to 'host'.  When I type man ns, it seems like it gives me the info for host.  host is not aliased with ns, and I can't figure out what to do short of re-installing it.

well i had experiances with the same problem for last 4 dayz now Alhumdulillah it is solved.. well wahat u have to do is ...
when u get the message to install "udo apt-get install host" **DONT DO THIS **
if u have already installed the host then u should remove it by using the command " sudo apt-get remove host"
then u have to reinstall the NS by using comand "./install" in the curent directory of NS..
plz do reply me if it works
best of luck

---

### Post by rizalutm on 2008-08-12
Hi, I'm in malaysia, study at University Technology of Malaysia - new user ubuntu and also NS2, for my dissertation I will use NS2. I have install NS2 in ubuntu, but when i want to run NS2 with command $ ns, I cannot, because ns in ubuntu, command for name server, anybody can help me???
tq

---

### Post by relikya on 2008-10-11
hi community, i have a similar problem with my ns2 on ubuntu 8.04.

I don't know what's the problem, i guess the path is ok, my message:

Usage:      host [-v] [-a] [-t querytype] [options]  name  [server]
Listing:    host [-v] [-a] [-t querytype] [options]  -l zone  [server]
Hostcount:  host [-v] [options] -H [-D] [-E] [-G] zone
Check soa:  host [-v] [options] -C zone
Addrcheck:  host [-v] [options] -A host
Listing options: [-L level] [-S] [-A] [-p] [-P prefserver] [-N skipzone]
Common options:  [-d] [-f|-F file] [-I chars] [-i|-n] [-q] [-Q] [-T] [-Z]
Other options:   [-c class] [-e] [-m] [-o] [-r] [-R] [-s secs] [-u] [-w]
Special options: [-O srcaddr] [-j minport] [-J maxport]
Extended usage:  [-x [name ...]] [-X server [name ...]]


I edit the path (bashrc) with the following lines:

# LD_LIBRARY_PATH
OTCL_LIB=/home/relikya/ns-allinone-2.33/otcl-1.13
NS2_LIB=/home/relikya/ns-allinone-2.33/lib
X11_LIB=/usr/X11R6/lib
USR_LOCAL_LIB=/usr/local/lib
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$OTCL_LIB:$NS2_LIB
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$X11_LIB:$USR_LOCAL_LIB

# TCL_LIBRARY
TCL_LIB=/home/relikya/ns-allinone-2.33/tcl8.4.18/library
USR_LIB=/usr/lib
export TCL_LIBRARY=$TCL_LIB:$USR_LIB

# PATH
XGRAPH=/home/relikya/ns-allinone-2.33/bin
XGRAPH=$XGRAPH:/home/relikya/ns-allinone-2.33/tcl8.4.18/unix
XGRAPH=$XGRAPH:/home/relikya/ns-allinone-2.33/tk8.4.18/unix
NS=/home/relikya/ns-allinone-2.33/ns-2.33/
NAM=/home/relikya/ns-allinone-2.33/nam-1.13/
PATH=$PATH:$XGRAPH:$NS:$NAM

or these lines

NS_HOME=/home/relikya/ns-allinone-2.33
export NS_HOME
PATH=$PATH:$NS_HOME/bin
export PATH

and they show me the same problem


I appreciate your help

---

### Post by neha21 on 2009-09-01
I'm also facing the same problem while running ns in Ubuntu......

Usage:      host [-v] [-a] [-t querytype] [options]  name  [server]
Listing:    host [-v] [-a] [-t querytype] [options]  -l zone  [server]
Hostcount:  host [-v] [options] -H [-D] [-E] [-G] zone
Check soa:  host [-v] [options] -C zone
Addrcheck:  host [-v] [options] -A host
Listing options: [-L level] [-S] [-A] [-p] [-P prefserver] [-N skipzone]
Common options:  [-d] [-f|-F file] [-I chars] [-i|-n] [-q] [-Q] [-T] [-Z]
Other options:   [-c class] [-e] [-m] [-o] [-r] [-R] [-s secs] [-u] [-w]
Special options: [-O srcaddr] [-j minport] [-J maxport]
Extended usage:  [-x [name ...]] server [name ...]]


I edit the path (bashrc) with the following lines:

# LD_LIBRARY_PATH
OTCL_LIB=/home/user/ns-allinone-2.33/otcl-1.13
NS2_LIB=/home/user/ns-allinone-2.33/lib
X11_LIB=/usr/X11R6/lib
USR_LOCAL_LIB=/usr/local/lib
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$OTCL_LIB:$NS2_LIB
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$X11_LIB:$USR_LOCAL_LIB

# TCL_LIBRARY
TCL_LIB=/home/user/ns-allinone-2.33/tcl8.4.18/library
USR_LIB=/usr/lib
export TCL_LIBRARY=$TCL_LIB:$USR_LIB

# PATH
XGRAPH=/home/user/ns-allinone-2.33/bin
XGRAPH=$XGRAPH:/home/user/ns-allinone-2.33/tcl8.4.18/unix
XGRAPH=$XGRAPH:/home/user/ns-allinone-2.33/tk8.4.18/unix
NS=/home/user/ns-allinone-2.33/ns-2.33/
NAM=/home/user/ns-allinone-2.33/nam-1.13/
PATH=$PATH:$XGRAPH:$NS:$NAM

PLz help me.....

---

### Post by Turin36 on 2009-10-28
Hello everybody,

I'm student and i have to make a project to compare two protocols in NS2,
MRSVP and M-YESSIR. Does anybody knows were i can find that patces?

Thanks a lot.
Constantine

---

### Post by pixel05 on 2009-11-07
i faced the same problem.. 
did the following and it got solved

>found which  ns process was running by typing- which ns
>it showed /usr/bin/ns
>removed ns from /usr/ns (rm ns)

then came back to the original directory and successfully ran $ns to get %

---

### Post by Scholar1987 on 2010-01-20
NS2 installation problems:

**I have run through all the installation steps required for installation of NS2.27 onto my system. But I face following problems**

Nam has been installed successfully.
ln: creating symbolic link `ns': File exists
ln: creating symbolic link `nam': File exists
Please compile your xgraph separately.
Please compile your gt-itm & sgb2ns separately.
Ns-allinone package has been installed successfully.
Here are the installation places:
tcl8.4.5:    /home/sawyer/ns-allinone-2.27/{bin,include,lib}
tk8.4.5:        /home/sawyer/ns-allinone-2.27/{bin,include,lib}
otcl:        /home/sawyer/ns-allinone-2.27/otcl-1.8
tclcl:        /home/sawyer/ns-allinone-2.27/tclcl-1.15
ns:        /home/sawyer/ns-allinone-2.27/ns-2.27/ns
nam:            /home/sawyer/ns-allinone-2.27/nam-1.10/nam

**but when I give it returns the following  **

sawyer@sawyer:~$ nam
nam: 
[code omitted because of length]
: no event type or button # or keysym
    while executing
"bind Listbox <MouseWheel> {
%W yview scroll [expr {- (%D / 120) * 4}] units
}"

[B]
And when I click on to installation paths above tcl8.4.5,tk8.4.5,ns,nam does not open. [/B]

What may be the problem !!! .

Next is when I go for validation that is after giving the command


sawyer@sawyer:~/ns-allinone-2.27/ns-2.27$ ./validate


Test output agrees with reference output
All test output agrees with reference output.
*** ./test-all-rng
Tests: rngtest
Running test rngtest:
../../ns test-suite-rng.tcl rngtest QUIET
Test output agrees with reference output
All test output agrees with reference output.
These messages are NOT errors and can be ignored:
    warning: using backward compatibility mode
    This test is not implemented in backward compatibility mode


validate overall report: some tests failed:
     ./test-all-newreno ./test-all-red
to re-run a specific test, cd tcl/test; ./test-all-TEST-NAME
Notice that some tests in webcache will fail on freebsd when -O is turned on.
This is due to some event reordering, which will disappear when -g is turned on.


Please let me know wat all are the extra packages to be installed. bcoz I am using old version of Ns2 on Ubuntu9.10

Thank you,
Sawyer

---

### Post by pricelesspri on 2010-03-22
Hi, 

I'm doing a project in ns2. I need some help with the commands. Is there any tutorial or link that gives a detailed understanding of the tcl scripts as we're unable to follow them much.
I would also like to know what the following command does..
 if {[$class info instprocs config] != ""} {
	$self config $ns
    }
This is in the test-suite-algorouting.tcl in ns2.

---

### Post by mirza_farid on 2010-06-20
edit the makefile.in and otcl folder file by adding the line in previous suggestion

---

### Post by aldreho on 2011-03-15
Hi
I need your help, I am using Ubuntu 10.10 that has installed on virtual box on my PC and I need to install NS2 on ubuntu10.10, but once I execute this command:

sudo apt-get install build-essential autoconf automake libxmu-dev

I receive this messages:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package autoconf is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Unable to locate package build-essential
E: Package 'autoconf' has no installation candidate
E: Unable to locate package automake
E: Unable to locate package libxmu-dev
w0090766@w0090766-VirtualBox:~/test/ns-allinone-2.34$

What is my mistake, or what I should do to install NS2 on this system?

---

### Post by ZeroAdam on 2011-03-15
Could you just install ns2 via the Ubuntu Software Center?

---

### Post by deelight1811 on 2012-10-02
hiii everyone...):P 'm new to tis community...
hv a prob badly need your help... plzzz do d needful
 i'm not able to run the tcl file.. i use ns-allinone-2.35 in u[COLOR=#000000][FONT=Ubuntu][COLOR=#3C3C3C]buntu 11.04[/COLOR][/FONT][/COLOR]
in terminal i got successfully installed  n ol.. wen i use the command 
ns
% //symbol appears then i give exit to which i get this line to which i type nam and i get //the following text
[COLOR=#000000][FONT=Ubuntu][COLOR=#3C3C3C][/COLOR][/FONT][/COLOR]deepa@deepa-Vostro-260s:~/ns-allinone-2.35$ nam
Cannot connect to existing nam instance. Starting a new one. . .
// a small window(black n grey in color) opens up with name "Nam console v1.15-RC4" with options File in the right and help in the left & some description about it


i just wanted to ask if i have installed ns2 correctly???
and how to execute a tcl file in it(if possi step by step plz)???

PLZZZZZ do help. . .!!!
loadzzz of thnx for reading my post:)

---

