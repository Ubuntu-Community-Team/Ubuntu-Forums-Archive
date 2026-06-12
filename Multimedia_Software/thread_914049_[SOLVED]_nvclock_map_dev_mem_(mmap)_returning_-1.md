---
title: "[SOLVED] nvclock: map_dev_mem (mmap) returning -1"
date: 2008-09-08
forum: Multimedia Software
---

### Post by jazzychad on 2008-09-08
Hi All,

I am trying to run nvclock on my system so that I can slow down the fans on my two GeForce 6600's (which currently sound like jet engines). I downloaded the latest source and compiled it. When it ran I always got a segfault. I narrowed down the problem to the map_dev_mem function in src/backend/back_linux.c It is always returning -1 (error code EINVAL). Of course this causes a segfault when something tries to access the mapped data (there is no check for invalid mmap return in the code).

Here are the relevant bits of code and the output it creates:

```
static void *map_dev_mem (int fd, unsigned long Base, unsigned long Size)
{
        void *base;
        int mapflags = MAP_SHARED;
        unsigned long realBase, alignOff;

        realBase = (Base & ~((unsigned long)getpagesize() - 1));
        alignOff = Base - realBase;


        CBE_FPRINTF(stderr, "...getpagesize is %u - mask is 0x%x...\n", getpagesize(), ~(getpagesize() - 1));
        CBE_FPRINTF(stderr, "...sizeof(Base) = %d...\n", sizeof(Base));
        CBE_FPRINTF(stderr, "...calling mmap with the following args: \n\t 0, %u, %d, %u (0x%x) - Base %u (0x%x)...\n", Size, fd, realBase, realBase, Base, Base);

        base = mmap((void  *)0, Size + alignOff, PROT_READ|PROT_WRITE,
                    mapflags, fd, (off_t)realBase);

        CBE_FPRINTF(stderr, "...map_dev_mem returning %p + %u...\n", base, alignOff);

        return (void *) ((char *)base + alignOff);
}

```

Output:

```
...getpagesize is 4096 - mask is 0xfffff000...
...sizeof(Base) = 4...
...calling mmap with the following args: 
         0, 4096, 3, 3356495872 (0xc8101000) - Base 3356495872 (0xc8101000)...
...map_dev_mem returning 0xffffffff + 0...

...getpagesize is 4096 - mask is 0xfffff000...
...sizeof(Base) = 4...
...calling mmap with the following args: 
         0, 4096, 3, 3356491776 (0xc8100000) - Base 3356491776 (0xc8100000)...
...map_dev_mem returning 0xffffffff + 0...

...getpagesize is 4096 - mask is 0xfffff000...
...sizeof(Base) = 4...
...calling mmap with the following args: 
         0, 196607, 3, 3355443200 (0xc8000000) - Base 3355443200 (0xc8000000)...
...map_dev_mem returning 0xffffffff + 0...

...getpagesize is 4096 - mask is 0xfffff000...
...sizeof(Base) = 4...
...calling mmap with the following args: 
         0, 8192, 3, 3361738752 (0xc8601000) - Base 3361738752 (0xc8601000)...
...map_dev_mem returning 0xffffffff + 0...

...getpagesize is 4096 - mask is 0xfffff000...
...sizeof(Base) = 4...
...calling mmap with the following args: 
         0, 8192, 3, 3362258944 (0xc8680000) - Base 3362258944 (0xc8680000)...
...map_dev_mem returning 0xffffffff + 0...

...getpagesize is 4096 - mask is 0xfffff000...
...sizeof(Base) = 4...
...calling mmap with the following args: 
         0, 65535, 3, 3358588928 (0xc8300000) - Base 3358588928 (0xc8300000)...
...map_dev_mem returning 0xffffffff + 0...
```

... where 0xffffffff of course means -1.

strace confirms the error (output for last mmap call):

```
mmap2(NULL, 65535, PROT_READ|PROT_WRITE, MAP_SHARED, 3, 0xc8300) = -1 EINVAL (Invalid argument)
```

Does anyone have any clue why this would be happening? /dev/nvidia0 and /dev/nvidia1 both exist and have rw permissions for everybody

System specs:
Ubuntu 7.10 i686
AMD Athlon XP 2400+
2GB RAM
Asus A8N-SLI Deluxe mobo
2x PNY nVidia GeForce 6600 SLI cards
nVidia drivers: 100.14.19 (latest restricted driver)

My overall goal is just to be able to control the fan speeds on the 6600's, but I haven't found any other methods except for everyone raving about nvclock.

Any help is appreciated. Thanks!

---

### Post by jazzychad on 2008-09-09
Thanks to Thunderbird (creator of nvclock), we figured out a workaround to the problem.  For completeness I will post the solution and hope that someone else finds it useful (mostly because it makes me very angry when somebody posts a question, then posts "I figured it out", and then doesn't post the solution).

Thunderbird said:
> Nvclock uses /dev/nvidia0 when it is available. The file is created when you load the nvidia kernel module but it is only activated when you enter X. If you don't have X running you could get this behavior. Nvclock can also use /dev/mem in such a case but that requires root ..

well, I figured out how to force /dev/mem

for those interested...

in backend/backend_linux.c around line 170, change the switch statement to switch(0) to force /dev/mem:

```
switch(0) //check_driver()                                                                                                                               
{
       case 0:
           nvclock.card[i].dev_name = (char*)strdup("/dev/mem");
           nvclock.card[i].reg_address = reg_addr;
           break;
        case 1:
           nvclock.card[i].dev_name = calloc(13, sizeof(char));
           sprintf(nvclock.card[i].dev_name, "/dev/nvidia%d", nvclock.card[i].number);
           nvclock.card[i].reg_address = 0;
           break;
         case 2:
           nvclock.card[i].dev_name = calloc(13, sizeof(char));
           sprintf(nvclock.card[i].dev_name, "/dev/nvidia%d", nvclock.card[i].number);
           nvclock.card[i].reg_address = reg_addr;
           break;
}
```

You have to run nvclock as root (or just sudo) after this change.

After that, the mmaps worked fine for me, and I was able to get the info on my cards.

Unfortunately, my 6600's don't support fanspeed adjustment as I was greeted an error message when I tried to slow them down. Bummer.

Oh well, I can always replace the fans, or just upgrade cards...

---

