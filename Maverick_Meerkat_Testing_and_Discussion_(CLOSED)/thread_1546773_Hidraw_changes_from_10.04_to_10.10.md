---
title: "Hidraw changes from 10.04 to 10.10"
date: 2010-08-05
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by sparker256 on 2010-08-05
I write plugins for X-Plane for Saitek panels. I was doing some testing on Maverick Meerkat have found a problem and not sure where to file the bug.

On the Saitek radio panel it has 4 five digit displays. I will include my test program and what I am seeing on the displays on 10.04 and 10.10.

What has appeared to change is the first char of the array is not displayed in 10.04. It has to be the correct number or I will get a broken pipe error.

Now on 10.10 it is displayed and works the same as it has to be a 1 for my radio panel, any other number will give broken pipe error.

Not sure what changed but am looking for a solution. 

```

int main (void) {
  unsigned char buf[3];
  int nr;
  int nw;
  int pos;
  int fd = -1;
  struct hidraw_devinfo dinfo;
  if ((fd = open("/dev/saitekradiopanel5", O_RDWR)) < 0) {
    perror("hidraw open");
    exit(1);
  }
  char wbuf[21] = {1, 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 0, 1, 2, 3, 4, 5, 6, 7, 8, 9};
  nw=write(fd, wbuf, sizeof(wbuf)); 
  if ( nw < 0 )
    { perror("write(stdout)"); exit(1); }
    if ( nw != 21 ) {
      fprintf(stderr, "Unsupported report length %d."
	      " Wrong hidraw device or kernel<2.6.26 ?\n", nw);
      exit(1);
    }
  close(fd);
  exit(0);
}

```


```

******************************************************************
******************   Display Info 10.04    ***********************

01234 56789
01234 56789

******************************************************************

******************************************************************
******************   Display Info 10.10    ***********************

10123 45678
90123 45678

******************************************************************

```


Bill

---

### Post by SevenMachines on 2010-08-06
maybe look at [hidraw: Use Interrupt Endpoint for OUT Transfers if Available]("http://git.kernel.org/?p=linux/kernel/git/next/linux-next.git;a=commit;h=a8ab5d58b0238b8199cc699b8dff7c5e1da24138")
which is vaguely related and is new. you might also want to try the [programming talk]("http://ubuntuforums.org/forumdisplay.php?f=39") forums.  
I've attached the 32-35 image diff for hid/hid-core.c and hid/usbhid/hid-core.c, but the above mentioned commit is the most obvious hiddraw change i can see

---

### Post by sparker256 on 2010-08-06
> **SevenMachines said:**
> maybe look at [hidraw: Use Interrupt Endpoint for OUT Transfers if Available]("http://git.kernel.org/?p=linux/kernel/git/next/linux-next.git;a=commit;h=a8ab5d58b0238b8199cc699b8dff7c5e1da24138")
which is vaguely related and is new. you might also want to try the [programming talk]("http://ubuntuforums.org/forumdisplay.php?f=39") forums.  
I've attached the 32-35 image diff for hid/hid-core.c and hid/usbhid/hid-core.c, but the above mentioned commit is the most obvious hiddraw change i can see

Thanks for your reply. I have posted in the programing talk before and been told that this is not a release so post here. Thankyou for the links and attachments. I wonder if I should contact Alan Ott or Jiri Kosina directly to ask if this is the expected response.

Thanks again Bill

---

### Post by Reiger on 2010-08-06
You *are* aware you are allocating a 24 char array with only 21 chars defined in the array initializer?

---

### Post by sparker256 on 2010-08-06
> **Reiger said:**
> You *are* aware you are allocating a 24 char array with only 21 chars defined in the array initializer?

I changed it to 21 but still have the same problem.

Bill

---

### Post by SevenMachines on 2010-08-07
> **Reiger said:**
> You *are* aware you are allocating a 24 char array with only 21 chars defined in the array initializer?

this is fine, as long as the write call has a sane length to it.

---

### Post by sparker256 on 2010-08-07
> **SevenMachines said:**
> this is fine, as long as the write call has a sane length to it.


I emailed Alan and we are working through my problem. It appears that there was a bug and my code deppended on the bug. Alan fixed the bug now I will have to fix my code. Thanks for your input and pointing me in the propper direction.

Bill

---

