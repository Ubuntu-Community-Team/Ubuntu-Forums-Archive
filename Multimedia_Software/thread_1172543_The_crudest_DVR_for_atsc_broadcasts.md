---
title: "The crudest DVR for atsc broadcasts"
date: 2009-05-28
forum: Multimedia Software
---

### Post by winterequinox on 2009-05-28
I've looked for a *simple* digital video recorder software program for my pchdtv 3000 for awhile.  I can never get mythtv to install.  I tried creating an iso of mythbuntu and installing and I couldn't even get the drop down menus to work, and mythtv would probably be overkill anyway.  I tried atscap but I couldn't get it to work.  About the only thing that would work is, in 1 terminal window to run "azap -r <some channel from .azap/channels.conf> and in another window to run "cat /dev/dvb/adapter0/dvr0 > x.mpg".

Sooo, I created a program to automate this, here's the source code:

#include <stdio.h>
#include <unistd.h>
#include <stdlib.h>
#include <errno.h>
#include <sys/types.h>
#include <signal.h>

int
main(int argc, char **argv)
{ pid_t pid1,pid2;
  int duration,waitTill;
	if (argc != 5)
	{
		fprintf(stderr, "%d args, need args for: "
			"channel, filename, wait, and duration\n",
			argc);
		exit(1);
	}
	waitTill = atoi(argv[3]);
	duration = atoi(argv[4]);
	if ((duration <= 0) || (waitTill < 0))
	{
		if (duration <=0 )
		{
			fprintf(stderr,"Invalid duration %d\n", duration);
		}
		if (waitTill < 0)
		{
			fprintf(stderr,"Invalid wait time %d\n", waitTill);
		}
		exit(1);
	}
	sleep(waitTill); /* Sleep till time to start recording */
	pid1 = fork();
	if (pid1 == 0) /* child, start azap */
	{ char commandBuff[100];
		sprintf(commandBuff,"azap -r %s",argv[1]);
		system(commandBuff);
	} else /* parent */
	{
		pid2 = fork();
		if (pid2 == 0) /* 2nd child start capture */
		{ char commandBuff[100];
			sleep(1);  /* make sure 1st child is well started */
			sprintf(commandBuff,"cat /dev/dvb/adapter0/dvr0 > %s",
				argv[2]);
			system(commandBuff);
		} else /* still parent wait till time to stop recording */
		{
			sleep(duration);
			/* stop children and die */
			kill(pid2,9);
			system("killall cat");
			sleep(1);
			kill(pid1,9);
			system("killall azap");
			sleep(1);
			exit(0);
		} /* end if still parent */
	} /* end if parent after 1st fork */
} /* end main */


Note it's a teensy bit dangerous in that if you're running cat in some other terminal window when it decides to terminate, it's issuing a "killall cat" command.  It's also issuing a "killall azap" command so if you have two or more dvb devices and you're running another azap, that will be killed also.  (Hey, I said this was crude.)

Let's say you call it "x.c".  You can compile it with "cc x.c -o x" to create an executable called 'x'.  Now, lets say you have a line in your .azap/channels.conf with SOMETV as the first field and in 15 seconds a half hour long program will start on SOMETV that you want to record.  You can invoke it as:
"x SOMETV sometv.prog.mpg 15 1800" where of course 30 minutes is 1800 seconds.  x has to be in your path.  If you've just compiled it into your home directory and $HOME or '~' is not in your $PATH, then you might invoke it as ./x SOMETV sometv.prog.mpg 15 1800.  Once you're convinced it works, move x to somewhere in your $PATH, like /usr/local/bin.

So it's crude, you invoke it and the azap part spits out stuff in your terminal window when it starts running.  You can get rid of that with 1>&2> /dev/null.  You can use at to start it later, with 0 second delay for instance, but **give a full path name for the output file** if you use at or make it a cron job.  ie:

echo "x SOMETV /tmp/sometv.mpg 0 1800 1>&2> /dev/null" | at 1pm

to start recording at 1:00PM and put sometv in /tmp.  You ought to be able to turn your computer off and just make sure it's turned on and rebooted by 1:00PM, maybe by setting something in the BIOS start menu, but beware, I haven't tried that myself yet.

For me, this is the just barely usable dvr for my computer.  Does anybody know of any other *simple* barebones dvr programs?  Something equivalent to 1970s vintage VCR?

---

### Post by xzero1 on 2009-05-28
You may be interested in my bash script that kinda does some of the same stuff for an hd-pvr device. It probably suffers the same 'kill a cat' problem but has other nice live monitoring features especially time left and file size prediction. The cat problem can probably be fixed -- all you need is the cat command's process id, then use that to kill it.

See
[http://ubuntuforums.org/showthread.php?t=1169204](http://ubuntuforums.org/showthread.php?t=1169204)

---

### Post by winterequinox on 2009-05-29
Thanks xzero1, that looks like a nice script.  That v4l2-ctl command looks pretty neat for hauppage devices.  I do have an hvr-950.  It was a dodgy business getting it to work on linux. (at least the pchdtv devices are *meant* to work with linux.)  I did get it working for awhile but then it quit after some software upgrade.  At first I blamed revisions to the kernel and other stuff.  Now I think it's just plain broken hardware.  I'll have to try it again sometime, but I'm just so damn lazy anymore.

Being lazy, my program was of course put together quickly.  I can think of ways to fix it up (have arguments for hours and minutes instead of just seconds fr'instance), and, as you mentioned, killing specific process ids instead of using 'killall'.  But, besides being lazy, I've fallen into the refinement trap of continuously improving programs in the past and I don't want to do it again.

I'm inexperienced in starting threads in the ubuntu forums, I probably should have put this thread in a dvb specific forum (anyway to move it now?)  If I ever do revise the program, I may put it in a new thread in a more appropriate forum.  In the mean time, I guess I was sorta hoping my crude program would inspire some younger guy to do the dirty work of cleaning it up, as long as they don't overdo it and make it too complicated with feature-itis.

Does this thing even need to be released under a license?  It should be a piece of cake to paraphrase it if it did.

---

### Post by xzero1 on 2009-06-01
I don't think that the v4l2-ctl is only for Hauppage devices. It seems to be an part of an api do access the hardware. As far a a license, I think that would be up to you. It is only your rights that would be protected.

---

