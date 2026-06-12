---
title: "doubt in select() in socket programming in C"
date: 2009-06-18
forum: Networking &amp; Wireless
---

### Post by polarbear12345 on 2009-06-18
suppose my server program has to deal with 1 listening socket and
1 stdin file descriptor eg.
while(1)
{
    //select initialization
    select(....args....);
    if(FD_ISSET(listenfd,&fd_rd))
       {
          //some initialization
          accept();
       }
    else if(FD_ISSET(stdin_fd,&fd_rd)
    {
          //do something
          I/O functions
    }
}

i wanna know if program is blocked in connect() or I/O functions and request for new connection arrives then that request will be stored in buffer maintained by listen() to be processed by select when program control **reenters** select or will it be lost.

similarly what if one of I/O fds become alive while program is blocked in connect() or I/O functions

---

### Post by Brandon Williams on 2009-06-18
I think you mean accept(), not connect(), since you would call accept as a result of the listenfd being readable.

If the listenfd is readable, then you will be able to accept immediately without blocking. There may be some edge condition that I'm not thinking about, though, so it would still be a good idea to mark listenfd non-blocking in order to ensure that it doesn't block.

The program may or may-not block when performing I/O on stdin, depending upon whether or not the specifics of the I/O operation. If there is data available but you ask for more than what is available, then it will still block. If you want async I/O, then you should use the aio calls defined by realtime posix. Start your investigation into this with 'man aio_read'.

If you do block in accept or some I/O call, both incoming connections and incoming data will be buffered, waiting for you to accept/read it. The buffer is not unlimited, though, so if you take too long, the buffers will fill.

---

