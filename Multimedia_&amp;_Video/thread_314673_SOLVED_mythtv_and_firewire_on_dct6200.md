---
title: "SOLVED: mythtv and firewire on dct6200"
date: 2006-12-07
forum: Multimedia &amp; Video
---

### Post by majoridiot on 2006-12-07
i have been fighting an ongoing battle to get an immediate and stable
firewire connection in mythtv on the motorola dct-6212.  believe me when
i say i have looked everywhere since first installing mythtv in august 
and i have tried *everything* to get a stable firewire link after a reboot
or stop/restart of the backend.

as it turns out, ALL of the information, scripts, etc. that i have been
relying on are WRONG because they insist point-to-point (p2p) connections
are the most reliable.  this may be true for some STBs but it certainly was
wrong in my case- broadcast runs FLAWLESSLY after reboot, starts, stops,
channel changes and pip/pip swaps.

how can you tell what's right for your firewire card/stb combo?  well,
thanks to jim westfall and an awesome firewire tester he wrote, you can 
diagnose and repair your firewire connection!

the following assumes you have a functional mythv frontend/backend
installed  with firewire capability.  you will also need build-essential,
libraw1394-dev and libiec61883-dev installed as well.

copy the following code into a text file and save it into the directory of 
your choice as **firewire_tester.c**

```
/*
 *  firewire_tester
 *  Copyright (c) 2006 by Jim Westfall
 *  Distributed as part of MythTV under GPL v2 and later.
 *
 *  $ gcc -Wall -o firewire_tester firewire_tester.c -liec61883 -lraw1394
 */

#include <unistd.h>
#include <stdlib.h>
#include <stdio.h>
#include <errno.h>
#include <sys/select.h>
#include <libraw1394/raw1394.h>
#include <libiec61883/iec61883.h>

#define ACTION_NONE        -1
#define ACTION_TEST_BCAST   0
#define ACTION_TEST_P2P     1
#define ACTION_FIX_BCAST    2
#define ACTION_RESET_BUS    3

#define SYNC_BYTE           0x47
#define MIN_PACKETS         25
#define MAX_NODATA          10

#define VERBOSE(args...)    do { if (verbose) printf(args); } while (0)

int verbose = 0;
int sync_failed = 0;
int nodata = 0;

static int read_packet (unsigned char *tspacket, int len, 
                        unsigned int dropped, void *callback_data)
{
    int *count = (int *)callback_data;

    if (dropped)
    {
        printf("Dropped %d packet(s).\n", dropped);
        return 0;
    }

    if (tspacket[0] != SYNC_BYTE)
    {
        sync_failed = 1;
        return 0;
    }
    nodata = 0;
    *count = *count + 1;
    return 1;
}

int test_connection(raw1394handle_t handle, int channel)
{
    int count = 0;
    int retry = 0;
    int fd = raw1394_get_fd(handle);
    iec61883_mpeg2_t mpeg;
    struct timeval tv;
    fd_set rfds;

    sync_failed = 0;
    mpeg = iec61883_mpeg2_recv_init(handle, read_packet, (void*) &count);
    iec61883_mpeg2_recv_start(mpeg, channel);
    while(count < MIN_PACKETS && retry < 2 && !sync_failed 
          && nodata < MAX_NODATA)
    {
        FD_ZERO(&rfds);
        FD_SET(fd, &rfds);
        tv.tv_sec = 1;
        tv.tv_usec = 0;

        if (select(fd + 1, &rfds, NULL, NULL, &tv) > 0)
        {
             nodata++;
             raw1394_loop_iterate(handle);
        }
        else
        {
            retry++;
        }
    }
    iec61883_mpeg2_recv_stop(mpeg);
    iec61883_mpeg2_close(mpeg);

    if (sync_failed)
        return 0;

    return count;
}

// create and test a p2p connection
// returns 1 on success, 0 on failure
int test_p2p(raw1394handle_t handle, nodeid_t node) {
    int channel, count, success = 0;
    channel = node;


    VERBOSE("P2P: Creating, node %d, channel %d\n", node, channel);

    printf("P2P: Testing...");
    fflush(stdout);
 
    // make connection
    if (iec61883_cmp_create_p2p_output(handle, node | 0xffc0, 0, channel,
                                       1 /* fix me, speed */ ) != 0)
    {
        printf("iec61883_cmp_create_p2p_output failed\n");
        return 0;
    }

    count = test_connection(handle, channel);
    if (count >= MIN_PACKETS)
    {
        printf("Success, %d packets received\n", count);
        success = 1;
    }
    else
    {
        printf("Failed%s\n", (sync_failed ? " (sync failed)":""));
    }

    VERBOSE("P2P: Disconnecting.\n");
    iec61883_cmp_disconnect(handle, node | 0xffc0, 0,
                            raw1394_get_local_id (handle),
                            -1, channel, 0);
    return success;
}

// create and test a broadcast connection
// returns 1 on success, 0 on failure
int test_broadcast(raw1394handle_t handle, nodeid_t node) {
    int channel, count, success = 0;
    channel = 63 - node;

    VERBOSE("Broadcast: Creating, node %d, channel %d\n", node, channel);

    printf("Broadcast: Testing...");
    fflush(stdout);

    // open connection
    if (iec61883_cmp_create_bcast_output(handle, node | 0xffc0, 0, channel, 
                                         1 /* fix me, speed */ ) != 0)
    {
        printf("iec61883_cmp_create_bcast_output failed\n");
        return 0;
    }
    count = test_connection(handle, channel);

    if (count >= MIN_PACKETS)
    {
        printf("Success, %d packets\n", count);
        success = 1;
    }
    else
    {
        printf("Failed%s\n", (sync_failed ? " (sync failed)":""));
    }

    VERBOSE("Broadcast: Disconnecting.\n");
    iec61883_cmp_disconnect(handle, node | 0xffc0, 0,
                            raw1394_get_local_id (handle),
                            -1, channel, 0);
    return success;
}  

/* 
 *  Attempt to get a reliable broadcast connection initialized
 *  This is done by first attempting multiple p2p connections until data is 
 *  received, once data is seen we then attempt multiple (5) broadcast 
 *  connections to verify the connection is stable.
 *  returns 1 on success, 0 on fail.
 */
int fix_broadcast(raw1394handle_t handle, nodeid_t node) {
    int p2p_retries = 0;
    int bcast_success = 0;

    // see if we even need to fix it
    while (test_broadcast(handle, node))
    {
        bcast_success++;
        if (bcast_success == 5)
        {
            printf("Broadcast Fix: Success (already stable)\n");
            return 1;
        }
    }

    // attempt upto 10 p2p connections looking for data
    while (p2p_retries < 10)
    { 
        if (test_p2p(handle, node))
        {
            // got data from p2p, try a few bcast connections
            bcast_success = 0;
            while (test_broadcast(handle, node))
            {
                bcast_success++;
                if (bcast_success == 5)
                {
                    printf("Broadcast Fix: Success\n");
                    return 1;
                }
            }
        }
        p2p_retries++;
    }
    printf("Broadcast Fix: Failed\n");
    return 0;
}

void usage(void) {
    printf("firewire_tester <action> -n <node> [-P <port>] [-r <n>] [-v]\n");
    printf(" Actions: (one is required)\n");
    printf("    -b          - test broadcast connection\n");
    printf("    -p          - test p2p connection\n");
    printf("    -B          - attempt to fix/stabilize broadcast connection\n");
    printf("    -R          - reset the firewire bus\n");
    printf(" Options\n");
    printf("    -n <node>   - firewire node, required\n");
    printf("    -P <port>   - firewire port, default 0\n");
    printf("    -r <n>      - run action <n> times, default 1\n");
    printf("    -v          - verbose\n");
    exit(1);
}

int main(int argc, char **argv) {
    raw1394handle_t handle;
    int node = -1;
    int port = 0;
    int runs = 1;
    int c, i, success;
    int action = ACTION_NONE;

    opterr = 0;
    while ((c = getopt(argc, argv, "Bbn:pP:r:Rv")) != -1)
    {
        switch (c) 
        {

            // attempt to get a reliable bcast connection initialize
            case 'B':
                if (action != ACTION_NONE)
                {
                    printf("Invalid command line\n");
                    usage();
                }
                action = ACTION_FIX_BCAST;
                break;

            // test broadcast connection
            case 'b':
                if (action != ACTION_NONE)
                {
                    printf("Invalid command line\n");
                    usage();
                }
                action = ACTION_TEST_BCAST;
                break;

            // set the node, required
            case 'n':
                node = atoi(optarg);
                if (node < 0 || node > 63)
                {
                    printf("Invalid node: %d\n", node);
                    exit(1);
                }
                break;

            // set the port, optional
            case 'P':
                port = atoi(optarg);
                if (port < 0)
                {
                    printf("Invalid port: %d\n", port);
                }
                break;

            // test a p2p connection
            case 'p':
                if (action != ACTION_NONE)
                {
                    printf("Invalid command line\n");
                    usage();
                }
                action = ACTION_TEST_P2P;
                break;

            case 'R':
                action = ACTION_RESET_BUS;
                break;

            // number of runs
            case 'r':
                runs = atoi(optarg);
                if (runs <= 0)
                {
                    printf("Run amount <= 0\n");
                    usage();
                }
                break;

            // verbose
            case 'v':
                verbose = 1;
                break;

            // bad option
            default:
                printf("Invalid command line\n");
                usage();
                
        }
    }

    if (action == ACTION_NONE)
    {
        usage();
    }

    if (action != ACTION_RESET_BUS && node == -1)
    {
        printf("-n <node> is a required option\n");
        usage();
    }

    VERBOSE("raw1394: Allocating handle, port %d.\n", port);
    handle = raw1394_new_handle_on_port(port);
    if (!handle)
    {
        printf("Failed to create new raw1394 handle on port %d\n", port);
        exit(1);
    }

    success = 0;
    switch (action)
    {
        case ACTION_TEST_BCAST:
            printf("Action: Test broadcast %d times, node %d, channel %d\n", 
                   runs, node, 63 - node);
            for (i = 0;i < runs;i++) 
                success += test_broadcast(handle, node);
            break;
        case ACTION_TEST_P2P:
            printf("Action: Test P2P connection %d times, node %d, channel %d\n",
                   runs, node, node);
            for (i = 0;i < runs;i++)
                success += test_p2p(handle, node);
            break;
        case ACTION_FIX_BCAST:
            printf("Action: Attempt to fix broadcast connection %d times, node %d\n", 
                   runs, node);
            for (i = 0;i < runs;i++)
                success += fix_broadcast(handle, node);
            break;
        case ACTION_RESET_BUS:
            runs = 1;
            printf("Action: Resetting the firewire bus\n");
            if (raw1394_reset_bus_new(handle, RAW1394_LONG_RESET) == 0)
            {
                printf("Bus reset succeeded\n");
                success = 1;
            }
            else
            {
                printf("Bus reset failed: %d\n", errno);
            }
            break;
    }

    VERBOSE("raw1394: Releasing handle.\n");
    raw1394_destroy_handle(handle);
    exit(!(success == runs));
}

```

from a terminal, execute the following to complile:

```
gcc -Wall -o firewire_tester firewire_tester.c -liec61883 -lraw1394
```

now you're ready to test your firewire to see what works best.  from the README:

firewire_tester <action> -n <node> [-P <port>] [-r <n>] [-v]

 Actions: (one is required)
    -b          - test broadcast connection
    -p          - test p2p connection
    -B          - attempt to fix/stabilize broadcast connection
    -R          - reset the firewire bus
 Options
    -n <node>   - firewire node, required
    -P <port>   - firewire port, default 0
    -r <n>      - run action <n> times, default 1
    -v          - verbose

There are 2 types of connections that can be used by mythtv to talk to 
the STB to transfer mpeg2 data.  These are peer 2 peer (P2P) and 
broadcast.  You will need to determine which works best with your STB.

Best bet is to start with trying P2P.  First thing to do is change the 
channel on your STB to a known non-encrypted channel, then run the 
tester multiple times testing a P2P connection.  If they all come back 
successful then have mythtv use P2P.  If you find that it fails, then 
move onto testing broadcast.  Start by doing the -B action to attempt 
fix/stabilize broadcast connection.  Once it has then test broadcast a 
few more times with -b action.

*(the following examples assume connection on adapter(port) 0, node 0... change to the appropriate settings for your system as identified by **plugreport**)*

example STB on node 0 that works best with a broadcast connection.

- test P2P connection a few times

```
$ ./firewire_tester -p -n 0 -r 5
```

Action: Test P2P connection 5 times, node 0, channel 0
P2P: Testing...Failed
P2P: Testing...Success, 46 packets received
P2P: Testing...Success, 164 packets received
P2P: Testing...Failed
P2P: Testing...Failed
- 2 out of 5 failed, not good.
- now use the -B option to try and fix/stabilize broadcast connection

```
$ ./firewire_tester -B -n 0
```

Action: Attempt to fix broadcast connection 1 times, node 0
Broadcast: Testing...Failed
P2P: Testing...Failed
P2P: Testing...Success, 58 packets received
Broadcast: Testing...Failed
P2P: Testing...Failed
P2P: Testing...Success, 48 packets received
Broadcast: Testing...Success, 75 packets
Broadcast: Testing...Success, 49 packets
Broadcast: Testing...Success, 42 packets
Broadcast: Testing...Success, 31 packets
Broadcast: Testing...Success, 112 packets
Broadcast Fix: Success
- worked! do a few more broadcast connection tests

```
$ ./firewire_tester -b -n 0 -r 5
```

Action: Test broadcast 5 times, node 0, channel 63
Broadcast: Testing...Success, 42 packets
Broadcast: Testing...Success, 112 packets
Broadcast: Testing...Success, 27 packets
Broadcast: Testing...Success, 78 packets
Broadcast: Testing...Success, 103 packets

and that's pretty much the result i got too.  armed with that info, i 
changed the p2p config for the firewire in mythtv-setup to broadcast, added
a ./firewire_tester line to my mythtv startup and kill/restart scripts and
all is well in the garden!  absolutely, rock-solid stable and NOT running 
p2p, as every how-to forum post, guide and wiki i read insisted.

again, a HUGE thanks to Jim Westfall for writing this great tool and 
proving that common knowledge is not one-size fits all.

source file and complete README are available at: [http://svn.mythtv.org/trac/browser/trunk/mythtv/contrib](http://svn.mythtv.org/trac/browser/trunk/mythtv/contrib)

additionally, according to jim, of the 10 6200 boxes he has personal experience with, 
**8 worked well with broadcast** and 2 worked with **both** broadcast
and p2p.  given that available "wisdom" says otherwise, someone might
consider making this a sticky.

---

### Post by newlinux on 2006-12-07
excellent information. I'm in the middle of building my first 2 mythboxes and I do want to do firewire capture with a similar box and I'll check this out, when I finally get to that step...

---

### Post by superm1 on 2006-12-08
Majoridiot, 

May your legacy live on..... consider yourself added to the Ubuntu documentation for mythtv: [https://help.ubuntu.com/community/MythTV_Edgy_Firewire](https://help.ubuntu.com/community/MythTV_Edgy_Firewire)

---

