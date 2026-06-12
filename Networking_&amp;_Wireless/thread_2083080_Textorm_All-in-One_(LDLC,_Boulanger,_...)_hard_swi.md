---
title: "Textorm All-in-One (LDLC, Boulanger, ...) hard switch usage"
date: 2012-11-11
forum: Networking &amp; Wireless
---

### Post by tybos on 2012-11-11
Hello Ubuntu forum users,

This is my first post and I'm quite confident that it will help some users out there !

I recently purchased an All-In-One in order to give my parents a simple, efficient, open-source solution to browse the internet ...

I downloaded and installed Ubuntu 12.10 without an issue and everything worked well (especially WIFI !!) ...

The PC was sold by LDLC.com under the reference > LDLC PC All In One Cybèle CC1-B8-2-H1 but all this *All In One Cybèle* family should behave the same as well as *Boulanger Essentiel b Smart'Station* line.
Those seem to be imported to France by Textorm ([www.textorm.com]("http://www.textorm.com")) but I guess they are imported under other brands in other countries.

The original contructor may be [Lengda]("http://www.lengdatek.com/detail.asp?ThisproductID=99&TengsoID=2027") .

The PC I got has wireless based on Atheros AR9002WB-1NG pci card (which contains AR9285 for Wifi and AR3011 for Bluetooth)

Wifi runs smoothly until I reboot or go to standby ! 
The ath9k driver seems to load well, but rfkill list gives a stressful 
```

#rfkill list all 
1: phy0: Wireless LAN     
    Soft blocked: no     
    Hard blocked: yes 
2: hci0: Bluetooth     
    Soft blocked: no     
    Hard blocked: no

```which means that some hardware switch is disabling wifi. Of course, there is no switch on the PC (except the Power one) and no Fn + Key.

A shutdown is necessary to unblock this switch but next reboot/standby will lock it again.


The Windows drivers provided with the PC use a touch button (on side of screen) to open a menu that is able to toggle this switch for Wifi, Bluetooth and Camera so I decided to reverse engineer this mechanism to see if it was possible to do the same under linux.


In fact, it uses an I/O port to toggle the 3 switches (Wifi, BT, Camera).

I managed to write a piece of C code that is able to manipulate these switches under Ubuntu.


Finally, the reason I post here is that I would like to know what to do next to bring a better support for such manipulations to Ubuntu or at least to Ubuntu wikis.

I can post C source code, but I need to clean it up first :P

---

### Post by Shadow aok on 2012-12-10
Hi,

Could you please post your piece of code ?

I'm facing the same issue and i can't make the touch buttons works under ubuntu.

Thanks.

---

### Post by tybos on 2012-12-11
OK,

Here is the source of a very tiny executable that makes the necessary IO accesses to either Enable or Disable desired switch :

```
#include <stdio.h>
#include <unistd.h>
#include <stdlib.h>
#include <sys/io.h>

// VALUE_PORT : IO port that manipulates the switches
#define VALUE_PORT    0x361
// LATCH_PORT : IO port that validates the changes
#define LATCH_PORT    0x6C


typedef enum{
    TOGGLE_IO_WIFI = 1,
    TOGGLE_IO_CAM = 4,
    TOGGLE_IO_BT = 8,
}TOGGLE_IO_t;

int main(int argc, char *argv[])
{
    int opt, tst;
    TOGGLE_IO_t readState, clearState = 0, setState = 0;

    while ((opt = getopt(argc, argv, "b:c:w:")) != -1)
    {
        switch (opt)
        {
        case 'b':
            tst = atoi(optarg);
            if (tst > 0)
                setState |= TOGGLE_IO_BT;
            else
                clearState |= TOGGLE_IO_BT;
            break;
        case 'c':
            tst = atoi(optarg);
            if (tst > 0)
                setState |= TOGGLE_IO_CAM;
            else
                clearState |= TOGGLE_IO_CAM;
            break;
        case 'w':
            tst = atoi(optarg);
            if (tst > 0)
                setState |= TOGGLE_IO_WIFI;
            else
                clearState |= TOGGLE_IO_WIFI;
            break;
        default: /* '?' */
            fprintf(stderr, "Usage: %s [-b {0,1}] [-c {0,1}] [-w {0,1}]\n",
                    argv[0]);
            return 1;
        }
    }

    if ((setState | clearState) != 0)
    {
        // Ask for permission to write to single byte ports
        if (ioperm(LATCH_PORT, 1, 1))
        {
            perror("ioperm latch");
            return 1;
        }
        if (ioperm(VALUE_PORT, 1, 1))
        {
            perror("ioperm value");
            return 1;
        }

        // Read current state
        readState = inb(VALUE_PORT);

        // Clear bits
        readState &= ~ clearState;

        // Set bits
        readState |= setState;

        // Write to port
        outb(readState, VALUE_PORT);
        // Validate change
        outb(0x12, LATCH_PORT);

        // Don't need access any more
        if (ioperm(LATCH_PORT, 1, 0))
        {
            perror("ioperm latch");
            return 1;
        }
        if (ioperm(VALUE_PORT, 1, 0))
        {
            perror("ioperm value");
            return 1;
        }
    }

    return 0;
}
```To compile, just call something like
```
gcc -Wall -O2 main.c -o toggle_io
```Usage is quite straightforward :

Call toggle_io with following options :
bluetooth : "-b 0" (disable) or "-b 1" (enable)
camera : "-c 0" or "-c 1"
wifi : "-w 0" or "-w 1"

Example : 
```
sudo ./toggle_io -w 1
```Hope this will help !

---

### Post by Shadow aok on 2012-12-13
I'll test it, thanks.
Right now i put a tiny usb wifi key to make it work.

---

