---
title: "C Program to establish PPP connection for bluetooth DUN"
date: 2011-02-24
forum: Networking &amp; Wireless
---

### Post by naveen.mdl on 2011-02-24
Hello everybody,
I can establish PPP connection by command *pon <options filename>. *Which takes the options defined in /etc/ppp/peers/<options filename> and script /etc/ppp/<script containg AT commads> bluetooth DUN connection(/dev/rfcomm0). But I want to write a Qt C++ program to start PPP connection with /dev/rfcomm0 and connect to internet.
I searched a lot in most of the forums and none of them were helpfull. Please help me out by guiding how to write the program, if possible please attach the code either c/c++ not a problem. Even DBUS concept is ok.

Regards
Naveen

---

### Post by naveen.mdl on 2011-02-28
Hello experts,
Dint u people find answer for my question?

---

### Post by dmizer on 2011-02-28
Have a look here: [http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html](http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html)

What you probably need is either gnome-ppp or wvdial.

I found this solution by googling for: "dial up networking ubuntu"

---

### Post by naveen.mdl on 2011-02-28
Thank you so much dmizer for your reply.
Well all the solutions in that link uses a tool to establish PPP connection. But in my case i should not use any tool. I need to create my own tool and include that in my QT application. That is i need to write a program including serial programming to send AT commands to establish PPP connection, which is the one followed in ***pon*** command. Otherwise there is also a method using Network Manager DBus concept. I found the code for Network Manger which is very huge and I really dont understand that and also i dont need all the types of connections to be done.
Only the mobile broadband connection has to be done.
Can you please suggest me in this regard.
Remember i dont want to use any of the comands in my program.

---

### Post by alexfish on 2011-02-28
Hi

possible need to have module installed

can look here see what you think

[http://qextserialport.sourceforge.net/](http://qextserialport.sourceforge.net/)

if you find it a problem . another area  to look at , process control using  tcl serial 

alexfish

ADDED : I am puzzled by this
> 
Remember i dont want to use any of the commands in my program.also added reference "Serial Programming Guide for POSIX Operating System"
[http://www.easysw.com/~mike/serial/serial.html]("http://www.easysw.com/%7Emike/serial/serial.html")

PPP

[http://www.koders.com/c/fidA7849C7E7424F2E1C3E86F85530F94C210781E7F.aspx?s=queue#L3](http://www.koders.com/c/fidA7849C7E7424F2E1C3E86F85530F94C210781E7F.aspx?s=queue#L3)

RFCOMM
[http://people.csail.mit.edu/albert/bluez-intro/x502.html](http://people.csail.mit.edu/albert/bluez-intro/x502.html)

---

### Post by naveen.mdl on 2011-03-02
Thank you for your reply.
The link given by you was good.
Before that I came to know while searching on net, that using pppLib.h we can initialise and start a PPP conncetion. but the problem is that i am not able to find that header file.
Is there any library which defines the APIs for calling PPP related functions from my C program?

---

### Post by ankith13 on 2011-03-02
hi
  you can probably go through this link
[http://www-kryo.desy.de/documents/vxWorks/V5.5/vxworks/ref/pppLib.html](http://www-kryo.desy.de/documents/vxWorks/V5.5/vxworks/ref/pppLib.html)
for finding more information on ppp library...
Let me know if there is still any problem...

Regards
Ankith

---

### Post by naveen.mdl on 2011-03-02
Hi, Ankith
Thanks for your quick reply. I had seen that link. But where can I get the header file(pppLib.h).

---

### Post by naveen.mdl on 2011-03-02
Ankith,
The library link which you have given is for the apple MAC os. Can we use that library for ubuntu too? Also pppLib.h has a included file #include<CoreFoundation>. But this is MAC os specific file. So i dont think I ca use those libraries in ubuntu. In some forum which i have, they have mentioned as no ppp libraries in ubuntu.
I am totally lost now. All the doors are closed for my work to progress. Please Help me out.

---

### Post by alexfish on 2011-03-03
Whilst on your quest can suggest looking at pppgundialler for gnome

of note in the sourcefiles are the pppd_wrap .h  and .c files

but all worth looking at in detail

[http://sourceforge.net/projects/gppp/](http://sourceforge.net/projects/gppp/)

Don't forget if "of use" give credits and acknowledgements  where due "Zoran Rilak  <bruce@tesla.rcub.bg.ac.yu>"

regards

alexfish

---

### Post by naveen.mdl on 2011-03-07
Hi Alex,
I am sorry for late reply, as i was out of station i couldnt do it.
Well i am going through the code in that link. I tried to configure that in my system but it says
"configure: error: cannot find install-sh or install.sh in . ./.. ./../.."
Tel me how to configure it successfully. Also let me know if there are some libraries(API) which can be used directly to start ppp connection using those APIs. I found pppLib.h but that is for MAC os. Definetely there must be a suitable libraery for ubuntu also. Please guide me in this regard.

---

### Post by naveen.mdl on 2011-03-08
Hi,
Alex, I configured it somehow by copying the instal-sh and some other files from /usr/share/automake folder. while i tried to make i was getting error like "modem.c: In function ‘script_handler’:
modem.c:50: error: ‘handle’ undeclared (first use in this function)"
"modem.c:50: error: expected ‘;’ before ‘modem’

In line 50 it says "!!! - Handle modem event."

and i commented that and tried once again.

now i got the error as
"modem.c: In function ‘script_handler’:
modem.c:55: error: ‘RECV_BUFFER_SIZE’ undeclared (first use in this function)"

and i added #define RECV_BUFFER_SIZE    1024 which was there in terminal.c file here. now i successfully compiled.
when i executer the gppp by ./gppp in src folder
i am able to see the dialog asking for username and password along with some settings. I set all the preferences and added a connection . my modem device is /dev/rfcomm0.
When i click connect it says initialisong and stays there itself without any response.
May be that i am not using the application correctly or is the problem with application itaelf. Please let me know.

---

### Post by alexfish on 2011-03-11
hi navine.mdl

the info , re links to c code are for   how the structures work ,

the original links to serial port "QextSerialPort" will be the easiest route to follow ,

this will give access to the libs at a higher level until experience is gained at terminos levels

re: example of QextSerialport : Qt forum 

[http://www.qtcentre.org/threads/22131-serial-port-communication-unstable-reading-%28SOLVED%29](http://www.qtcentre.org/threads/22131-serial-port-communication-unstable-reading-%28SOLVED%29)


as a little helper / this is my own chat using tcl / the basic structure is the same , but this uses Buffering and tty control , notice the use of flush serial (buffer) + the timings

```
 ##########################################################
 # PROC :Chat 
 ##########################################################
 proc Chat {tty cmds} {
    set tty [string trim $tty]
    set isdev [string first /dev/tty $tty]
        if {$isdev  > -1} {set tty $tty}
        if {$isdev == -1} {set tty "/dev/$tty"}    
    if { [catch {set serial [open $tty RDWR]} fid] } {
           puts  "\n$tty : $fid \n"
        return
    } else {
    ##################################################
    # set the port to stnd 115200 buffering DTR 1
    ##################################################
    fconfigure $serial -mode "115200,n,8,1"
    fconfigure $serial -blocking 0 -buffering full -ttycontrol {RTS 0 DTR 1}
    after 100
    foreach cmd $cmds {
        #puts "$tty: $cmd"
        puts $serial $cmd
        after 10
        flush $serial
        after 10
        set data6 [read $serial]
        #set data [string trim $data]
        puts $data6
        after 10
    }
    close $serial}
    return
}
```

---

