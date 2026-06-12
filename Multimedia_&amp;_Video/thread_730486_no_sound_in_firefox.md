---
title: "no sound in firefox"
date: 2008-03-20
forum: Multimedia &amp; Video
---

### Post by ac3raven on 2008-03-20
I know there are tons of posts about this but I have tried seemingly every solution i could find.  I tried changing the owner of firefox, i tried changing the owner of flash, i tried opening firefox as root, i tried the pulse audio solution, I tried the libflashsupport install, i tried the asound.blahblah thing, i tried editing firefoxrc, I tried disabling esd.  NONE OF THESE ARE WORKING, how do I fix flash????

I installed all the pulse audo files from synaptic and tried installing it with pretty much no results, I tried it without root and got the same result:

root@starbuck:/home/glenn# cd libflashsupport-1.2
root@starbuck:/home/glenn/libflashsupport-1.2# make sudoinstall
gcc -fPIC -shared -O2 -Wall -Werror  -lpthread -DLIBDIR=/usr/lib \
        -DALSA_INTERNAL  -DPULSEAUDIO -DLIBPULSEPATH='"/usr/lib/libpulse-simple.so.0"' -DESD -DLIBESDPATH='"/usr/lib/libesd.so.0"' \
        -DOSS -DOPENSSL -lssl  \
        flashsupport.c -o libflashsupport.so
flashsupport.c:200:25: error: openssl/ssl.h: No such file or directory
flashsupport.c:225:17: error: esd.h: No such file or directory
flashsupport.c:290: error: expected ‘)’ before ‘format’
flashsupport.c: In function ‘FPX_SoundOutput_Detect’:
flashsupport.c:476: error: ‘FPX_esd_play_stream_fallback’ undeclared (first use in this function)
flashsupport.c:476: error: (Each undeclared identifier is reported only once
flashsupport.c:476: error: for each function it appears in.)
cc1: warnings being treated as errors
flashsupport.c: In function ‘FPX_Init’:
flashsupport.c:669: warning: implicit declaration of function ‘SSL_library_init’
flashsupport.c: At top level:
flashsupport.c:692: error: expected specifier-qualifier-list before ‘SSL’
flashsupport.c: In function ‘FPX_SSLSocket_Create’:
flashsupport.c:702: error: ‘struct SSL_Instance’ has no member named ‘sslCtx’
flashsupport.c:702: warning: implicit declaration of function ‘SSL_CTX_new’
flashsupport.c:702: warning: implicit declaration of function ‘TLSv1_client_method’
flashsupport.c:704: error: ‘struct SSL_Instance’ has no member named ‘ssl’
flashsupport.c:704: warning: implicit declaration of function ‘SSL_new’
flashsupport.c:704: error: ‘struct SSL_Instance’ has no member named ‘sslCtx’
flashsupport.c:706: warning: implicit declaration of function ‘SSL_set_fd’
flashsupport.c:706: error: ‘struct SSL_Instance’ has no member named ‘ssl’
flashsupport.c:710: error: ‘struct SSL_Instance’ has no member named ‘ssl’
flashsupport.c:711: warning: implicit declaration of function ‘SSL_shutdown’
flashsupport.c:711: error: ‘struct SSL_Instance’ has no member named ‘ssl’
flashsupport.c:714: error: ‘struct SSL_Instance’ has no member named ‘sslCtx’
flashsupport.c:715: warning: implicit declaration of function ‘SSL_CTX_free’
flashsupport.c:715: error: ‘struct SSL_Instance’ has no member named ‘sslCtx’
flashsupport.c: In function ‘FPX_SSLSocket_Destroy’:
flashsupport.c:729: error: ‘struct SSL_Instance’ has no member named ‘ssl’
flashsupport.c:730: error: ‘struct SSL_Instance’ has no member named ‘ssl’
flashsupport.c:733: error: ‘struct SSL_Instance’ has no member named ‘sslCtx’
flashsupport.c:734: error: ‘struct SSL_Instance’ has no member named ‘sslCtx’
flashsupport.c: In function ‘FPX_SSLSocket_Connect’:
flashsupport.c:750: warning: implicit declaration of function ‘SSL_connect’
flashsupport.c:750: error: ‘struct SSL_Instance’ has no member named ‘ssl’
flashsupport.c: In function ‘FPX_SSLSocket_Receive’:
flashsupport.c:762: warning: implicit declaration of function ‘SSL_read’
flashsupport.c:762: error: ‘struct SSL_Instance’ has no member named ‘ssl’
flashsupport.c: In function ‘FPX_SSLSocket_Send’:
flashsupport.c:774: warning: implicit declaration of function ‘SSL_write’
flashsupport.c:774: error: ‘struct SSL_Instance’ has no member named ‘ssl’
flashsupport.c: In function ‘ESD_FPX_SoundOutput_Open’:
flashsupport.c:1251: error: ‘ESD_DEFAULT_RATE’ undeclared (first use in this function)
flashsupport.c:1253: error: ‘ESD_BITS16’ undeclared (first use in this function)
flashsupport.c:1253: error: ‘ESD_STEREO’ undeclared (first use in this function)
flashsupport.c:1254: error: ‘ESD_STREAM’ undeclared (first use in this function)
flashsupport.c:1254: error: ‘ESD_PLAY’ undeclared (first use in this function)
flashsupport.c:1255: error: ‘esd_format_t’ undeclared (first use in this function)
flashsupport.c:1255: error: expected ‘;’ before ‘format’
flashsupport.c:1263: error: ‘format’ undeclared (first use in this function)
flashsupport.c:1271: warning: implicit declaration of function ‘FPX_esd_play_stream_fallback’
make: *** [libflashsupport.so] Error 1

---

### Post by DJ_Peng on 2008-03-21
Do you have the totem-mozilla plugin installed? That's always been what got my Firefox to stop being mute.

---

### Post by Yellow Pasque on 2008-03-21
There seem to be a lot of error messages related to the Enlightenment Sound Daemon (ESD).

Go to System -> Preferences -> Sound. Under the second tab, uncheck the box for software sound mixing. Click 'OK', log out and log back in. See if that does the trick.

The bad part about this workaround is that you probably won't be able to play multiple sounds at the same time or you might have issues with "Devices busy"

EDIT: Also, install SSL so that libflashsupport can work.
```
sudo apt-get install libssl0.9.8 libssl-dev
```

---

### Post by ac3raven on 2008-03-21
I've have the totem plugin, but I don't have the totem movie player, instead I have vlc because I like it more.  I have the vlc firefox plugin as well, and I have already tried disabling esd, no luck there, and that download to get libflashsupport working shows no results either.

---

### Post by DJ_Peng on 2008-03-21
The VLC plugin is what I have in Firefox/Hardy. Not sure why you aren't getting sound, but I'm sure someone should be around before too long that has run into your situation and knows just how to fix it.

---

### Post by Yellow Pasque on 2008-03-21
```
cd ~/libflashsupport-1.2
gksudo (<-- if root permissions needed) gedit flashsupport.c
```
Put // in front of the #define SSL line and do not use the -lssl flag in the compilation command.
Are you using x86_64?

---

### Post by ac3raven on 2008-03-21
I don't have a #define SSL line and I don't see -lssl anywhere aside from in a comment at the top.  I'm x86.

---

### Post by ac3raven on 2008-03-21
*/
////////////////////////////////////////////////////////////////////////////////////////////////////
//
// File name: flashsupport.c
// Targets: Adobe Flash Player 9.1 beta 2 for Linux (9.0.21.78)
// Last Revision Date: 11/20/2006
//

////////////////////////////////////////////////////////////////////////////////////////////////////
//
// These are the feature which can be turned on and off. They are all
// optional. The ALSA and Video4Linux support in this file is somewhat
// redundant and reduced in functionality as the Flash Player already has
// ALSA and Video4Linux support built-in. It is provided here for reference only.
// enable OSS here as it will override it.
//

// Default library location
/*
#ifndef LIBPULSEPATH
#define LIBPULSEPATH /usr/lib/libpulse-simple.so.0
#endif 

#ifndef LIBESDPATH
#define LIBESDPATH /usr/lib/libesd.so.0
#endif
*/

/* Do not define these here, but rather in the Makefile 
//#define OPENSSL
#define GNUTLS
#define V4L1
#define PULSEAUDIO
#define ESD
#define OSS
#define ALSA_INTERNAL
#define ALSA
*/

////////////////////////////////////////////////////////////////////////////////////////////////////
//
// To compile and install flashsupport.c the following components are required:
//
//  - a C compiler (gcc 4.03 is known to be working)
//  - OpenSSL developer package and working user libraries (OpenSSL 0.9.8 is known to be working)
//  - OSS (or ALSA) developer package and working users libraries (Linux 2.6.15 is known to be working)
//  - sudo or root access to install the generated library to /usr/lib
//
// We suggest these steps in a terminal:
//
// > cc -shared -O2 -Wall -Werror -lssl flashsupport.c -o libflashsupport.so
// > ldd libflashplayer.so
// > sudo cp libflashplayer.so /usr/lib
//
// Make sure that 'ldd' can resolve all dynamic libraries. Otherwise the Flash Player
// will silently fail to load and use libflashsupport.so.
//

////////////////////////////////////////////////////////////////////////////////////////////////////
//
// SHARED SECTION, DO NOT CHANGE!
//
#ifdef cplusplus
extern "C" {
#endif // cplusplus

//
// Imported functions
//

typedef void *(*T_FPI_Mem_Alloc)(int size);	// This function is not thread safe
typedef void (*T_FPI_Mem_Free)(void *ptr); // This function is not thread safe

#if defined(ALSA) || defined(OSS) || defined(ESD) || defined(PULSEAUDIO)
typedef void (*T_FPI_SoundOutput_FillBuffer)(void *ptr, char *buffer, int n_bytes); // This function is thread safe
#endif // defined(ALSA) || defined(OSS) || defined(ESD) || defined(PULSEAUDIO)

struct FPI_Functions {
	int	  fpi_count;
	void *fpi_mem_alloc; 				// 1
	void *fpi_mem_free;					// 2
	void *fpi_soundoutput_fillbuffer;	// 3
};

//
// Exported functions
//

void *FPX_Init(void *ptr);

static void FPX_Shutdown(void);

#if defined(OPENSSL) || defined(GNUTLS)
static void *FPX_SSLSocket_Create(int socket_fd);
static int FPX_SSLSocket_Destroy(void *ptr);
static int FPX_SSLSocket_Connect(void *ptr);
static int FPX_SSLSocket_Receive(void *ptr, char *buffer, int n_bytes);
static int FPX_SSLSocket_Send(void *ptr, const char *buffer, int n_bytes);
#endif // defined(OPENSSL) || defined(GNUTLS)

#if defined(ALSA)
static void *ALSA_FPX_SoundOutput_Open(void);
static int ALSA_FPX_SoundOutput_Close(void *ptr);
static int ALSA_FPX_SoundOutput_Latency(void *ptr);
#endif // defined(ALSA)

#if defined(OSS)
static void *OSS_FPX_SoundOutput_Open(void);
static int OSS_FPX_SoundOutput_Close(void *ptr);
static int OSS_FPX_SoundOutput_Latency(void *ptr);
#endif // defined(OSS)

#if defined(ESD)
static void *ESD_FPX_SoundOutput_Open(void);
static int ESD_FPX_SoundOutput_Close(void *ptr);
static int ESD_FPX_SoundOutput_Latency(void *ptr);
#endif // defined(ESD)

#if defined(PULSEAUDIO)
static void *PULSEAUDIO_FPX_SoundOutput_Open(void);
static int PULSEAUDIO_FPX_SoundOutput_Close(void *ptr);
static int PULSEAUDIO_FPX_SoundOutput_Latency(void *ptr);
#endif // defined(PULSEAUDIO)

#ifdef V4L1
static void *FPX_VideoInput_Open();
static int FPX_VideoInput_Close(void *ptr);
static int FPX_VideoInput_GetFrame(void *ptr, char *data, int width, int height, int pitch_n_bytes);
#endif // V4L1

struct FPX_Functions {
	int   fpx_count;
	void *fpx_shutdown;					// 1
	void *fpx_sslsocket_create;			// 2
	void *fpx_sslsocket_destroy;		// 3
	void *fpx_sslsocket_connect;		// 4
	void *fpx_sslsocket_receive;		// 5
	void *fpx_sslsocket_send;			// 6
	void *fpx_soundoutput_open;			// 7
	void *fpx_soundoutput_close;		// 8
	void *fpx_soundoutput_latency;		// 9
	void *fpx_videoinput_open;			// 10
	void *fpx_videoinput_close;			// 11
	void *fpx_videoinput_getframe;		// 12
};

#ifdef cplusplus
};
#endif // cplusplus
//
// END OF SHARED SECTION
//
////////////////////////////////////////////////////////////////////////////////////////////////////

#include <memory.h>
#include <stdio.h>
#include <dlfcn.h>

#ifdef OPENSSL
#include <openssl/ssl.h>
#elif defined(GNUTLS)
#include <sys/types.h>
#include <sys/socket.h>
#include <arpa/inet.h>
#include <unistd.h>
#include <gnutls/gnutls.h>
#endif // GNUTLS

#ifdef ALSA
#include <pthread.h>
#include <semaphore.h>
#include <alsa/asoundlib.h>
#endif

#if defined(OSS)
#include <unistd.h>
#include <pthread.h>
#include <linux/soundcard.h>
#include <sys/ioctl.h>
#include <fcntl.h>
#endif

#if defined(ESD)
#include <unistd.h>
#include <esd.h>
#include <pthread.h>
#include <signal.h>
#include <dlfcn.h>
#endif

#if defined(PULSEAUDIO)
#include <pulse/simple.h>
#include <pulse/error.h>
#include <unistd.h>
#include <pthread.h>
#endif

#ifdef V4L1
#include <unistd.h>
#include <pthread.h>
#include <linux/videodev.h>
#include <sys/ioctl.h>
#include <fcntl.h>
#endif // V4L1

//Includes for output driver detection
#if defined(ALSA) || defined(OSS) || defined(ESD) || defined(PULSEAUDIO)
#include <stdlib.h> //getenv
#include <sys/types.h> //stat
#include <sys/stat.h> //stat
#include <unistd.h> //stat
#endif // defined(ALSA) || defined(OSS) || defined(ESD) || defined(PULSEAUDIO)

static struct FPX_Functions fpx_functions;

static T_FPI_Mem_Alloc FPI_Mem_Alloc = 0;
static T_FPI_Mem_Free FPI_Mem_Free = 0;

#if defined(ALSA) || defined(OSS) || defined(ESD) || defined(PULSEAUDIO)
static T_FPI_SoundOutput_FillBuffer FPI_SoundOutput_FillBuffer = 0;
#endif // defined(ALSA) || defined(OSS) || defined(ESD) || defined(PULSEAUDIO)

#if defined(ALSA) || defined(OSS) || defined(ESD) || defined(PULSEAUDIO)
/* JMD: Choose between multiple audio interfaces by order of priority:
- Pulse is always first, since it can support esound, gstreamer, alsa, oss
  and jack and is easily identified by environment variables or socket.
  Supports full audio/video synchronization, even over the network.
- Esound is second, since it's by default in many distributions, and supports
  oss. NOTE: audio and video are not synchronized, since the latency
  functions can hang the browser.
- Arts (TODO) is next. It's not currently supported because it's being
  phased out. Besides, it can use Esound as a backend
- NASD: Not supported for the moment, there is not much information
  available...
- Jack (TODO). When it's done, it should go after Pulse, but before ALSA.
- ALSA: default if it's supported
- Finally, if nothing else, fallback on oss
*/

#define AUDIO_PULSE 128
#define AUDIO_ESD 64
#define AUDIO_ARTS 32
#define AUDIO_NAS 16
#define AUDIO_JACK 8
#define AUDIO_ALSA 2
#define AUDIO_OSS 1

#if defined(ESD)
//ESD functions
int (*FPX_esd_play_stream_fallback)( esd_format_t format, int rate,
	const char *host, const char *name );
#endif
#if defined(PULSEAUDIO)
//PULSE functions
pa_simple* (*FPX_pa_simple_new) (const char *server,const char *name,
    pa_stream_direction_t dir,const char *dev,const char *stream_name,
    const pa_sample_spec *ss,const pa_channel_map *map,
    const pa_buffer_attr *attr,int *error);

void (*FPX_pa_simple_free) (pa_simple *s);

int (*FPX_pa_simple_write) (pa_simple *s, const void*data, size_t length, int *error);

int (*FPX_pa_simple_drain) (pa_simple *s, int *error);

int (*FPX_pa_simple_read) (pa_simple *s, void*data, size_t length, int *error);

pa_usec_t (*FPX_pa_simple_get_latency) (pa_simple *s, int *error);

int (*FPX_pa_simple_flush) (pa_simple *s, int *error);

const char* (*FPX_pa_strerror) (int error);
#endif
                     
static int audiotype=2;
static int audiodrivers=0;
static int audiodebug=0;
static int pulsedebug=0;

void FPX_SoundOutput_Detect()
{
	char *tmpenv;
	struct stat buf;
#if defined(PULSEAUDIO) || defined(ESD)
	void *handle;
	char *error;	
#endif 
#if defined(PULSEAUDIO)
	char tmpstr[1024]="";
#endif
	if((tmpenv=getenv("FLASH_AUDIODEBUG"))!=NULL) {
		audiodebug=1;
	}
	if((tmpenv=getenv("FLASH_PULSEDEBUG"))!=NULL) {
		pulsedebug=1;
	}

	if(audiodebug) {
		fprintf( stderr,"Flash sound output detection routine.\n");
		fprintf( stderr,"(c) 2006 Revolution Linux inc,\n");
		fprintf( stderr,"Jean-Michel Dault <jmdault@revolutionlinux.com>\n");
	}

#if defined(PULSEAUDIO)
	//Check if PULSE AUDIO is running
	if((tmpenv=getenv("USER"))!=NULL) {
		strcpy(tmpstr,"/tmp/pulse-");
		strcat(tmpstr,tmpenv);
		if(!stat(tmpstr,&buf)) {
			if(audiodebug) fprintf( stderr, "PulseAudio socket found\n");
			audiodrivers = audiodrivers | AUDIO_PULSE;
		}
	}
	//Check if PULSE AUDIO is running system-wide
	strcpy(tmpstr,"/var/lib/run/pulse/native");
	if(!stat(tmpstr,&buf)) {
		if(audiodebug) fprintf( stderr, "PulseAudio system-wide found\n");
		audiodrivers = audiodrivers | AUDIO_PULSE;
	}
	//Pulse over network
	if((tmpenv=getenv("PULSE_SERVER"))!=NULL) {
		if(audiodebug) fprintf( stderr, "PulseAudio SERVER variable present\n");
		audiodrivers = audiodrivers | AUDIO_PULSE;
	}
	//Pulse autospawn daemon
	if((tmpenv=getenv("PULSE_BINARY"))!=NULL) {
		if(audiodebug) fprintf( stderr, "PulseAudio BINARY variable present\n");
		audiodrivers = audiodrivers | AUDIO_PULSE;
	}
#endif
#if defined(ESD)
	//Check if ESD is running
	if(!stat("/tmp/.esd/socket",&buf)) {
		if(audiodebug) fprintf( stderr, "ESD socket found\n");
		audiodrivers = audiodrivers | AUDIO_ESD;
	}
	//ESD over network
	if((tmpenv=getenv("ESPEAKER"))!=NULL) {
		if(audiodebug) fprintf( stderr, "ESD variable ESPEAKER found\n");
		audiodrivers = audiodrivers | AUDIO_ESD;
	}

#endif
#if defined(ALSA) || defined(ALSA_INTERNAL)
	//Check for ALSA device
	if(!stat("/proc/asound",&buf)) {
		if(audiodebug) fprintf( stderr, "ALSA device detected\n");
		audiodrivers = audiodrivers | AUDIO_ALSA;
	}
#endif
#if defined(OSS)
	//Check for OSS device
	if(!stat("/dev/dsp",&buf)) {
		if(audiodebug) fprintf( stderr, "OSS device present\n");
		audiodrivers = audiodrivers | AUDIO_OSS;
	}
#endif

	if((tmpenv=getenv("FLASH_FORCE_PULSEAUDIO"))!=NULL) {
#if defined(PULSEAUDIO)
			if(audiodebug) fprintf( stderr, "Forcing PulseAudio\n");
			audiodrivers = AUDIO_PULSE;
#else
			if(audiodebug) fprintf( stderr, "PulseAudio unavailable: please recompile libflashsupport.so!\n");			
#endif
	}

	if((tmpenv=getenv("FLASH_FORCE_ESD"))!=NULL) {
#if defined(ESD)
			if(audiodebug) fprintf( stderr, "Forcing ESD\n");			
			audiodrivers = AUDIO_ESD;
#else
			if(audiodebug) fprintf( stderr, "ESD unavailable: please recompile libflashsupport.so!\n");			
#endif
	}

	if((tmpenv=getenv("FLASH_FORCE_ALSA"))!=NULL) {
#if defined(ALSA) || defined(ALSA_INTERNAL)
			if(audiodebug) fprintf( stderr, "Forcing ALSA\n");			
			audiodrivers = AUDIO_ALSA;
#else
			if(audiodebug) fprintf( stderr, "ALSA unavailable: please recompile libflashsupport.so!\n");			
#endif
	}

	if((tmpenv=getenv("FLASH_FORCE_OSS"))!=NULL) {
#if defined(OSS)
			if(audiodebug) fprintf( stderr, "Forcing OSS\n");			
			audiodrivers = AUDIO_OSS;
#else
			if(audiodebug) fprintf( stderr, "OSS unavailable: please recompile libflashsupport.so!\n");			
#endif
	}

//Check for required libraries and functions
#if defined(PULSEAUDIO)
	if((audiodrivers & AUDIO_PULSE) && !FPX_pa_simple_new) {
		handle = dlopen(LIBPULSEPATH, RTLD_LAZY);
		if (!handle) {
			if(audiodebug) fprintf(stderr,"Can't load %s: %s\n",LIBPULSEPATH,dlerror());
			audiodrivers = audiodrivers & (~AUDIO_PULSE);
		}
		FPX_pa_simple_new = dlsym(handle, "pa_simple_new");
		if ((error = dlerror()) != NULL) {
			if(audiodebug) fprintf(stderr, "%s\n", error);
			audiodrivers = audiodrivers & (~AUDIO_PULSE);
		}
		FPX_pa_simple_write = dlsym(handle, "pa_simple_write");
		if ((error = dlerror()) != NULL) {
			if(audiodebug) fprintf(stderr, "%s\n", error);
			audiodrivers = audiodrivers & (~AUDIO_PULSE);
		}
		FPX_pa_simple_drain = dlsym(handle, "pa_simple_drain");
		if ((error = dlerror()) != NULL) {
			if(audiodebug) fprintf(stderr, "%s\n", error);
			audiodrivers = audiodrivers & (~AUDIO_PULSE);
		}
		FPX_pa_simple_free = dlsym(handle, "pa_simple_free");
		if ((error = dlerror()) != NULL) {
			if(audiodebug) fprintf(stderr, "%s\n", error);
			audiodrivers = audiodrivers & (~AUDIO_PULSE);
		}
		FPX_pa_simple_get_latency = dlsym(handle, "pa_simple_get_latency");
		if ((error = dlerror()) != NULL) {
			if(audiodebug) fprintf(stderr, "%s\n", error);
			audiodrivers = audiodrivers & (~AUDIO_PULSE);
		}
		FPX_pa_strerror = dlsym(handle, "pa_strerror");
		if ((error = dlerror()) != NULL) {
			if(audiodebug) fprintf(stderr, "%s\n", error);
			audiodrivers = audiodrivers & (~AUDIO_PULSE);
		}
	}
#endif
#if defined(ESD)
	if((audiodrivers & AUDIO_ESD) && !FPX_esd_play_stream_fallback) {
		handle = dlopen(LIBESDPATH, RTLD_LAZY);
		if (!handle) {
			if(audiodebug) fprintf(stderr,"Can't load %s: %s\n",LIBESDPATH,dlerror());
			audiodrivers = audiodrivers & (~AUDIO_ESD);
		}
		FPX_esd_play_stream_fallback = dlsym(handle, "esd_play_stream_fallback");
		if ((error = dlerror()) != NULL) {
			if(audiodebug) fprintf(stderr, "%s\n", error);
			audiodrivers = audiodrivers & (~AUDIO_ESD);
		}
	}
#endif

	return;
}

static void *FPX_SoundOutput_Open(void)
{
	void *ptr;

	if(audiodebug) fprintf( stderr,"audiodrivers=%d\n",audiodrivers);	
#if defined(PULSEAUDIO)
	if(audiodrivers & AUDIO_PULSE) {
		if(audiodebug) fprintf( stderr,"Trying PULSE\n");	
		ptr=PULSEAUDIO_FPX_SoundOutput_Open();
		if(audiodebug) fprintf( stderr,"ptr=%d\n",(int)ptr);	
		if(ptr) {
			audiotype=AUDIO_PULSE;
			if(audiodebug) fprintf( stderr, "Using PulseAudio driver\n");
			return ptr;
		}
	}
#endif
#if defined(ESD)
	if(audiodrivers & AUDIO_ESD) {
		if(audiodebug) fprintf( stderr,"Trying ESD\n");	
		ptr=ESD_FPX_SoundOutput_Open();
		if(audiodebug) fprintf( stderr,"ptr=%d\n",(int)ptr);	
		if(ptr) {
			audiotype=AUDIO_ESD;
			if(audiodebug) fprintf( stderr, "Using Esound audio driver\n");
			return ptr;
		}
	}
#endif
#if defined(ALSA_INTERNAL)
	if(audiodrivers & AUDIO_ALSA) {
		if(audiodebug) fprintf( stderr,"Using *INTERNAL* ALSA\n");	
		return 0;
	}
#endif
#if defined(ALSA)
	if(audiodrivers & AUDIO_ALSA) {
		if(audiodebug) fprintf( stderr,"Trying ALSA\n");	
		ptr=ALSA_FPX_SoundOutput_Open();
		if(audiodebug) fprintf( stderr,"ptr=%d\n",(int)ptr);	
		if(ptr) {
			audiotype=AUDIO_ALSA;
			if(audiodebug) fprintf( stderr, "Using ALSA audio driver\n");
			return ptr;
		}
	}
#endif
#if defined(OSS)
	if(audiodrivers & AUDIO_OSS) {
		if(audiodebug) fprintf( stderr,"Trying OSS\n");	
		ptr=OSS_FPX_SoundOutput_Open();
		if(audiodebug) fprintf( stderr,"ptr=%d\n",(int)ptr);	
		if(ptr) {
			audiotype=AUDIO_OSS;
			if(audiodebug) fprintf( stderr, "Using OSS audio driver\n");
			return ptr;
		}
	}
#endif
	// No sound...
	if(audiodebug) fprintf( stderr, "NO SOUND DRIVER! Revert to internal ALSA driver!\n");
	return 0;
}

static int FPX_SoundOutput_Close(void *ptr)
{
	int retcode;
#if defined(PULSEAUDIO)
	if(audiotype == AUDIO_PULSE) {
		retcode=PULSEAUDIO_FPX_SoundOutput_Close(ptr);
		return retcode;
	}
#endif
#if defined(ESD)	
	if(audiotype == AUDIO_ESD) {
		retcode=ESD_FPX_SoundOutput_Close(ptr);
		return retcode;
	}
#endif
#if defined(ALSA)
	if(audiotype == AUDIO_ALSA) {
		retcode=ALSA_FPX_SoundOutput_Close(ptr);
		return retcode;
	}
#endif
#if defined(OSS)	
	if(audiotype == AUDIO_OSS) {
		retcode=OSS_FPX_SoundOutput_Close(ptr);
		return retcode;
	}
#endif
	return 0;
}

static int FPX_SoundOutput_Latency(void *ptr)
{
	int retcode;
#if defined(PULSEAUDIO)
	if(audiotype == AUDIO_PULSE) {
		retcode=PULSEAUDIO_FPX_SoundOutput_Latency(ptr);
		return retcode;
	}
#endif
#if defined(ESD)
	if(audiotype == AUDIO_ESD) {
		retcode=ESD_FPX_SoundOutput_Latency(ptr);
		return retcode;
	}
#endif
#if defined(ALSA)	
	if(audiotype == AUDIO_ALSA) {
		retcode=ALSA_FPX_SoundOutput_Latency(ptr);
		return retcode;
	}
#endif
#if defined(OSS)	
	if(audiotype == AUDIO_OSS) {
		retcode=OSS_FPX_SoundOutput_Latency(ptr);
		return retcode;
	}
#endif
	return 0;
}
#endif // defined(ALSA) || defined(OSS) || defined(ESD) || defined(PULSEAUDIO)

void *FPX_Init(void *ptr)
{
#if defined(ALSA) || defined(OSS) || defined(ESD) || defined(PULSEAUDIO)
	FPX_SoundOutput_Detect();
#endif // defined(ALSA) || defined(OSS) || defined(ESD) || defined(PULSEAUDIO)
	if ( !ptr ) return 0;

	//
	// Setup imported functions
	//

	struct FPI_Functions *fpi_functions = (struct FPI_Functions *)ptr;

	if ( fpi_functions->fpi_count >= 1 )	FPI_Mem_Alloc 		= fpi_functions->fpi_mem_alloc; 					// 1
	if ( fpi_functions->fpi_count >= 2 )	FPI_Mem_Free 		= fpi_functions->fpi_mem_free;  					// 2

#if defined(ALSA) || defined(OSS) || defined(ESD) || defined(PULSEAUDIO)
	if ( fpi_functions->fpi_count >= 3 )	FPI_SoundOutput_FillBuffer= fpi_functions->fpi_soundoutput_fillbuffer;  // 3
#endif // defined(ALSA) || defined(OSS) || defined(ESD) || defined(PULSEAUDIO)

	//
	// Setup exported functions
	//

	memset(&fpx_functions, 0, sizeof(fpx_functions));

	fpx_functions.fpx_shutdown		 			= FPX_Shutdown;					// 1

#if defined(OPENSSL) || defined(GNUTLS)
	fpx_functions.fpx_sslsocket_create 			= FPX_SSLSocket_Create;			// 2
	fpx_functions.fpx_sslsocket_destroy 		= FPX_SSLSocket_Destroy;		// 3
	fpx_functions.fpx_sslsocket_connect 		= FPX_SSLSocket_Connect;		// 4
	fpx_functions.fpx_sslsocket_receive 		= FPX_SSLSocket_Receive;		// 5
	fpx_functions.fpx_sslsocket_send 			= FPX_SSLSocket_Send;			// 6
#endif // defined(OPENSSL) || defined(GNUTLS)

#if defined(ALSA) || defined(OSS) || defined(ESD) || defined(PULSEAUDIO)
	fpx_functions.fpx_soundoutput_open 			= FPX_SoundOutput_Open;			// 7
	fpx_functions.fpx_soundoutput_close 		= FPX_SoundOutput_Close;		// 8
	fpx_functions.fpx_soundoutput_latency 		= FPX_SoundOutput_Latency;		// 9
#endif // defined(ALSA) || defined(OSS) || defined(ESD) || defined(PULSEAUDIO)

#ifdef V4L1
	fpx_functions.fpx_videoinput_open			= FPX_VideoInput_Open;			// 10
	fpx_functions.fpx_videoinput_close			= FPX_VideoInput_Close;			// 11
	fpx_functions.fpx_videoinput_getframe		= FPX_VideoInput_GetFrame;		// 12
#endif // V4L1

	fpx_functions.fpx_count						= 14;

#ifdef OPENSSL
	SSL_library_init();
#elif defined(GNUTLS)
	gnutls_global_init();
#endif // GNUTLS

	return (void *)&fpx_functions;
}

static void FPX_Shutdown()
{
#ifdef OPENSSL

#elif defined(GNUTLS)
	gnutls_global_deinit();
#endif // GNUTLS
}

//
// SSL support functions
//

#ifdef OPENSSL
struct SSL_Instance {
	SSL 	*ssl;
	SSL_CTX *sslCtx;
};

static void *FPX_SSLSocket_Create(int socket_fd)
	// return = instance pointer
{
	struct SSL_Instance *instance = (struct SSL_Instance *)FPI_Mem_Alloc(sizeof(struct SSL_Instance));
	memset(instance,0,sizeof(struct SSL_Instance));
fprintf(stderr,"AAAAAAAAAA\n");
	if ( ( instance->sslCtx = SSL_CTX_new( TLSv1_client_method() ) ) == 0 ) goto fail;

	if ( ( instance->ssl = SSL_new(instance->sslCtx) ) == 0 ) goto fail;

	if ( SSL_set_fd(instance->ssl, socket_fd) < 0 ) goto fail;

	return (void *)instance;
fail:
	if ( instance->ssl ) {
		SSL_shutdown(instance->ssl);
	}

	if ( instance->sslCtx ) {
		SSL_CTX_free(instance->sslCtx);
	}

	if (FPI_Mem_Free) FPI_Mem_Free(instance);

	return 0;
}

static int FPX_SSLSocket_Destroy(void *ptr)
	// ptr = instance pointer
	// return = 0 on sucess, < 0 on error
{
	struct SSL_Instance *instance = (struct SSL_Instance *)ptr;

	if ( instance->ssl ) {
		SSL_shutdown(instance->ssl);
	}

	if ( instance->sslCtx ) {
		SSL_CTX_free(instance->sslCtx);
	}

	if (FPI_Mem_Free) FPI_Mem_Free(instance);

	return 0;
}

static int FPX_SSLSocket_Connect(void *ptr)
	// ptr = instance pointer
	// socket_fd = BSD socket fd to be associated with SSL connection
	// return = 0 on sucess, < 0 on error
	//
	// Flash Player will use errno to obtain current status
{
	struct SSL_Instance *instance = (struct SSL_Instance *)ptr;
	return SSL_connect(instance->ssl);
}

static int FPX_SSLSocket_Receive(void *ptr, char *buffer, int n_bytes)
	// ptr = instance pointer
	// buffer = raw buffer to place received data into
	// n_bytes = length of buffer in bytes
	// return = actual bytes received, < 0 on error
	//
	// Flash Player will use errno to obtain current status
{
	struct SSL_Instance *instance = (struct SSL_Instance *)ptr;
	return SSL_read(instance->ssl, buffer, n_bytes);
}

static int FPX_SSLSocket_Send(void *ptr, const char *buffer, int n_bytes)
	// ptr = instance pointer
	// buffer = raw buffer to be sent
	// n_bytes = length of input buffer in bytes
	// return = actual bytes sent, < 0 on error
	//
	// Flash Player will use errno to obtain current status
{
	struct SSL_Instance *instance = (struct SSL_Instance *)ptr;
	return SSL_write(instance->ssl, buffer, n_bytes);
}
#elif defined(GNUTLS)
struct SSL_Instance {
	gnutls_session_t 					session;
	gnutls_anon_client_credentials_t 	anoncred;
};

static void *FPX_SSLSocket_Create(int socket_fd)
	// return = instance pointer
{
	const int kx_prio[] = { GNUTLS_KX_ANON_DH, 0 };

	struct SSL_Instance *instance = (struct SSL_Instance *)FPI_Mem_Alloc(sizeof(struct SSL_Instance));
	memset(instance,0,sizeof(struct SSL_Instance));

	if ( gnutls_anon_allocate_client_credentials(&instance->anoncred) < 0 ) goto fail;

	if ( gnutls_init(&instance->session, GNUTLS_CLIENT) < 0 ) goto fail;

	if ( gnutls_set_default_priority(instance->session) < 0 ) goto fail;

	if ( gnutls_kx_set_priority(instance->session, kx_prio) < 0 ) goto fail;

	if ( gnutls_credentials_set(instance->session, GNUTLS_CRD_ANON, instance->anoncred) < 0 ) goto fail;

	gnutls_transport_set_ptr(instance->session, (gnutls_transport_ptr_t)socket_fd);

	return (void *)instance;
fail:

	if ( instance->session ) {
		gnutls_deinit(instance->session);
	}

	if ( instance->anoncred ) {
		gnutls_anon_free_client_credentials(instance->anoncred);
	}

	if (FPI_Mem_Free) FPI_Mem_Free(instance);

	return 0;
}

static int FPX_SSLSocket_Destroy(void *ptr)
	// ptr = instance pointer
	// return = 0 on sucess, < 0 on error
{
	struct SSL_Instance *instance = (struct SSL_Instance *)FPI_Mem_Alloc(sizeof(struct SSL_Instance));

	gnutls_bye(instance->session, GNUTLS_SHUT_RDWR);

	gnutls_deinit(instance->session);

	gnutls_anon_free_client_credentials(instance->anoncred);

	if (FPI_Mem_Free) FPI_Mem_Free(instance);

	return 0;
}

static int FPX_SSLSocket_Connect(void *ptr)
	// ptr = instance pointer
	// socket_fd = BSD socket fd to be associated with SSL connection
	// return = 0 on sucess, < 0 on error
	//
	// Flash Player will use errno to obtain current status
{
	struct SSL_Instance *instance = (struct SSL_Instance *)ptr;
	return gnutls_handshake(instance->session);
}

static int FPX_SSLSocket_Receive(void *ptr, char *buffer, int n_bytes)
	// ptr = instance pointer
	// buffer = raw buffer to place received data into
	// n_bytes = length of buffer in bytes
	// return = actual bytes received, < 0 on error
	//
	// Flash Player will use errno to obtain current status
{
	struct SSL_Instance *instance = (struct SSL_Instance *)ptr;
	return gnutls_record_recv(instance->session, buffer, n_bytes);
}

static int FPX_SSLSocket_Send(void *ptr, const char *buffer, int n_bytes)
	// ptr = instance pointer
	// buffer = raw buffer to be sent
	// n_bytes = length of input buffer in bytes
	// return = actual bytes sent, < 0 on error
	//
	// Flash Player will use errno to obtain current status
{
	struct SSL_Instance *instance = (struct SSL_Instance *)ptr;
	return gnutls_record_send(instance->session, buffer, n_bytes);
}
#endif // GNUTLS

//
// Sound support functions
//


#ifdef ALSA
struct ALSA_SoundOutput_Instance {
	snd_pcm_t *				handle;
	snd_async_handler_t *	async_handler;
	sem_t 					semaphore;
	pthread_t 				thread;
	char *					buffer;
	snd_pcm_sframes_t 		buffer_size;
	snd_pcm_sframes_t 		period_size;
	snd_pcm_sframes_t               buffer_pos;
	char *                                  buffer_ptr;
};

static void *alsa_thread(void *ptr)
{
	struct ALSA_SoundOutput_Instance *instance = (struct ALSA_SoundOutput_Instance *)ptr;
	snd_pcm_sframes_t avail = 0;
	int result = 0;
	int err = 0;
	int state = 0;

	for( ; ; ) {

		err = sem_wait(&instance->semaphore);
		if ( !instance->handle ) {
			pthread_exit(0);
			return 0;
		}
		
		if ( err < 0 ) {
			usleep(1);
			continue;
		}

		do {
			if ( instance->buffer_pos <= 0 ) {
				FPI_SoundOutput_FillBuffer(ptr, instance->buffer, snd_pcm_frames_to_bytes(instance->handle, instance->period_size));
				instance->buffer_pos = instance->period_size;
				instance->buffer_ptr = instance->buffer;
			}
			do {
				state = snd_pcm_state(instance->handle);
				if(state != SND_PCM_STATE_RUNNING && state != SND_PCM_STATE_PREPARED) {
					snd_pcm_prepare(instance->handle);
				}
				result = snd_pcm_writei(instance->handle, instance->buffer_ptr, instance->buffer_pos);
				if( result <= 0 ) {
					switch( result ) {
						case	-EPIPE: {
									snd_pcm_prepare(instance->handle);
								} break;
						case	-ESTRPIPE: {
									err = snd_pcm_resume(instance->handle);
									if ( err < 0 ) {
										snd_pcm_prepare(instance->handle);
									}
								} break;
					}
					break;
				} else {
					instance->buffer_pos -= result;
					instance->buffer_ptr += snd_pcm_frames_to_bytes(instance->handle, result);
				}
			} while (instance->buffer_pos);
			avail = snd_pcm_avail_update(instance->handle);
			if( avail < 0 ) {
				switch( avail ) {
					case	-EPIPE: {
								snd_pcm_prepare(instance->handle);
							} break;
					case	-ESTRPIPE: {
								err = snd_pcm_resume(instance->handle);
								if ( err < 0 ) {
									snd_pcm_prepare(instance->handle);
								}
							} break;
				}
				break;
			}

		} while(avail >= instance->period_size);
	}
}

static void alsa_callback(snd_async_handler_t *ahandler)
{
	struct ALSA_SoundOutput_Instance *instance = (struct ALSA_SoundOutput_Instance *)snd_async_handler_get_callback_private(ahandler);
	// signal mixer thread
	sem_post(&instance->semaphore);
}

static void *ALSA_FPX_SoundOutput_Open()
	// return = instance pointer
{
	struct ALSA_SoundOutput_Instance *instance = 0;
	snd_pcm_hw_params_t *hwparams = 0;
	snd_pcm_sw_params_t *swparams = 0;
	snd_pcm_format_t pcm_format;
	unsigned int buffer_time = 500000;
	unsigned int period_time =  20000;
	unsigned int actual_rate;
	snd_pcm_uframes_t size;
	int direction;
	void *retVal = 0;
	int err = 0;

	if ( !FPI_SoundOutput_FillBuffer )  goto fail;
	if ( !FPI_Mem_Alloc ) goto fail;

	instance = FPI_Mem_Alloc(sizeof(struct ALSA_SoundOutput_Instance));
	memset(instance,0,sizeof(struct ALSA_SoundOutput_Instance));

	if ( ( err = snd_pcm_open(&instance->handle, "default", SND_PCM_STREAM_PLAYBACK, SND_PCM_NONBLOCK) ) < 0) {
		if ( ( err = snd_pcm_open(&instance->handle, "plughw:0,0", SND_PCM_STREAM_PLAYBACK, SND_PCM_NONBLOCK) ) < 0) {
			goto fail;
		}
	}

	snd_pcm_hw_params_alloca(&hwparams);
	snd_pcm_sw_params_alloca(&swparams);

	if (snd_pcm_hw_params_any(instance->handle, hwparams) < 0) goto fail;

	if (snd_pcm_hw_params_set_access(instance->handle, hwparams, SND_PCM_ACCESS_RW_INTERLEAVED) < 0) goto fail;

	pcm_format = SND_PCM_FORMAT_S16_LE;

	if (snd_pcm_hw_params_set_format(instance->handle, hwparams, pcm_format) < 0) goto fail;

	if (snd_pcm_hw_params_set_channels(instance->handle, hwparams, 2) < 0) goto fail;

	actual_rate = 44100;

	if (snd_pcm_hw_params_set_rate_near(instance->handle, hwparams, &actual_rate, 0) < 0) goto fail;

---

### Post by ac3raven on 2008-03-30
so...any solutions?

---

### Post by DJ_Peng on 2008-03-30
I've got nothing. I've been hoping someone else has something for you.

---

### Post by ac3raven on 2008-04-02
[IMG][[IMG]http://img138.imageshack.us/img138/950/soundvi6.th.png[/IMG]](http://img138.imageshack.us/my.php?image=soundvi6.png)[/IMG]

The ADC sound servers are the only ones from the list that work.  Maybe that has something to do with it.  Maybe Firefox is just confused because of this audio server.  I'm just throwing that out there, I don't have a clue what could be wrong.

---

### Post by ac3raven on 2008-04-02
root@starbuck:/home/glenn# firefox
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave
AND SO ON THE SAME MESSAGE ABOUT 100 MORE TIMES.

that's what I get when I run FF as root, still no sound in flash.  Absent the sad faces, although they are very fitting.

---

### Post by twright on 2008-04-02
try this (with pulseaudio):
```
wget http://pulseaudio.vdbonline.net/flashplugin-nonfree-pulse_0.1~000.tar.gz
tar xvfz flashplugin-nonfree-pulse_0.1~000.tar.gz
cd flashplugin-nonfree-pulse-0.1~000
sudo apt-get install libpulse-dev
make
sudo make install

```

[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

---

### Post by ac3raven on 2008-04-02
nope didn't work, already tried that:

glenn@starbuck:~$ wget [http://pulseaudio.vdbonline.net/flashplugin-nonfree-pulse_0.1~000.tar.gz](http://pulseaudio.vdbonline.net/flashplugin-nonfree-pulse_0.1~000.tar.gz)
--16:27:06--  [http://pulseaudio.vdbonline.net/flashplugin-nonfree-pulse_0.1~000.tar.gz](http://pulseaudio.vdbonline.net/flashplugin-nonfree-pulse_0.1~000.tar.gz)
           => `flashplugin-nonfree-pulse_0.1~000.tar.gz'
Resolving pulseaudio.vdbonline.net... 208.78.101.188
Connecting to pulseaudio.vdbonline.net|208.78.101.188|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5,109 (5.0K) [application/x-gzip]

100%[====================================>] 5,109         --.--K/s             

16:27:06 (121.36 KB/s) - `flashplugin-nonfree-pulse_0.1~000.tar.gz' saved [5109/5109]

glenn@starbuck:~$ tar xvfz flashplugin-nonfree-pulse_0.1~000.tar.gz
flashplugin-nonfree-pulse-0.1~000/
flashplugin-nonfree-pulse-0.1~000/flashsupport.c
flashplugin-nonfree-pulse-0.1~000/debian/
flashplugin-nonfree-pulse-0.1~000/debian/compat
flashplugin-nonfree-pulse-0.1~000/debian/changelog
flashplugin-nonfree-pulse-0.1~000/debian/overrides/
flashplugin-nonfree-pulse-0.1~000/debian/overrides/flashplugin-nonfree-pulse
flashplugin-nonfree-pulse-0.1~000/debian/rules
flashplugin-nonfree-pulse-0.1~000/debian/copyright
flashplugin-nonfree-pulse-0.1~000/debian/control
flashplugin-nonfree-pulse-0.1~000/Makefile
glenn@starbuck:~$ cd flashplugin-nonfree-pulse-0.1~000
glenn@starbuck:~/flashplugin-nonfree-pulse-0.1~000$ sudo apt-get install libpulse-dev
[sudo] password for glenn:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libpulse-dev is already the newest version.
The following packages were automatically installed and are no longer required:
  libxine1-x mplayer-skins libsvga1 fftw3 libxine1-misc-plugins libxcb-xv0
  mysql-common libmysqlclient15off ruby1.8 libxcb1 ruby libcurl3 libggi2
  libgii1 libxcb-shape0 libgtk2-gladexml-perl libtunepimp5 libifp4
  libgii1-target-x libxine1-plugins libxvmc1 libpq5 libruby1.8 libxcb-shm0
  libnjb5 libofa0 libxine1-console libxine1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
glenn@starbuck:~/flashplugin-nonfree-pulse-0.1~000$ make
cc -shared -O0 -Wall -Wextra -W `pkg-config --cflags libpulse` -g `pkg-config --libs libpulse` flashsupport.c -o libflashsupport.so
glenn@starbuck:~/flashplugin-nonfree-pulse-0.1~000$ sudo make install
install -D -m 644 libflashsupport.so /usr/lib/libflashsupport.so
glenn@starbuck:~/flashplugin-nonfree-pulse-0.1~000$

---

### Post by the_analyzer on 2008-04-04
hey what the **** is the ubuntu develpment team is doing now? ou yea they're doing  8.04 and dont give a **** about sound issues. Nobody that will have problems with sound will keep ubuntu. 
Hoping for solution. 
PS: I have this problemm too and Im very angry. :)

---

### Post by twright on 2008-04-04
have you submitted a bug report?

otherwise the devs won't even know about the issue

---

### Post by the_analyzer on 2008-04-04
Yes, but for some bugs, anyway, there are hundreds or thousands with these kinds of problems (sound, flash without sound, crash, etc etc) and many submit these bugs, but few are being fixed.

---

### Post by ac3raven on 2008-04-05
I'm pretty sure I've tried every solution known to man and flash sound still doesn't work.  There has to be something I'm not doing.

---

### Post by ac3raven on 2008-04-05
Frakin a, now its magically working.  I have noticed something I should point out:  usually my login music doesn't play, but when it does, flash audio seems to work as well, so considering I'm using a sound card with ALSA drivers, I bet it has something to do with sound server confusion at some point.

---

### Post by ac3raven on 2008-04-06
Okay, I plugged my speakers into the on board sound, and it immediately started working, no restart required.  So it's definitely something with my sound card drivers, so where to now?

---

