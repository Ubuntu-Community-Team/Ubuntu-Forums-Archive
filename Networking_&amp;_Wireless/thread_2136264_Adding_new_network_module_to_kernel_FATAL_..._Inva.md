---
title: "Adding new network module to kernel: FATAL: ... Invalid argument"
date: 2013-04-17
forum: Networking &amp; Wireless
---

### Post by taylorr4 on 2013-04-17
Hello,

I am trying to compile and install the UMTS network module ([http://lagarcavilla.org/software/rrc.html](http://lagarcavilla.org/software/rrc.html)) for my Ubuntu 10.04 (kernel 2.6.38.8) box but I am having issues when I try to load the load the (modprobe sch_rrc) into the kernel.

The above UMTS network module was designed for kernel 2.6.18, so I had to report the sch_rrc.c patch file to be compatible with the current kernel I am using. I believe I successfully did this and managed to build a new kernel with the patches added. 

The problem is that whenever I try to add the sch_rrc module i get the following error:

sudo modprobe -b sch_rrc
FATAL: Error inserting sch_rrc (/lib/modules/2.6.38.8-rrc/kernel/net/sched/sch_rrc.ko): Invalid argument

On checking dmesg, I simply get:
[11605.541430] rrc: version 0.1

like the module has been added, but it hasn't. It is not under lsmod.

I then tried adding the module by using insmod:
/lib/modules/2.6.38.8-rrc/kernel/net/sched$ sudo insmod sch_rrc.ko
insmod: error inserting 'sch_rrc.ko': -1 Invalid parameters

and this time I get invalid parameters. I think there must be a compatibility error in the sch_rrc.c file with the newer k ernel 2.6.38.8. But I cant seem to find out where as the error messages are very ambiguous.

Any help would be greatly appreciated, I am pretty stuck at the moment on this.

I will add the code of my modified sch_rrc.c file to the bottom of this post

Thanks,
Richard

/*
 * net/sched/sch_rrc.c    UMTS RRC State Machine emulator
 *
 *         This program is free software; you can redistribute it and/or
 *         modify it under the terms of the GNU General Public License
 *         as published by the Free Software Foundation; either version
 *         2 of the License, or (at your option) any later version.
 *
 *          Many of the algorithms and ideas for this came from
 *        NIST Net which is not copyrighted. 
 *
 * Author:    Andres Lagar-Cavilla <andres@lagarcavilla.org>
 */

#include <linux/module.h>
#include <linux/slab.h>
#include <linux/types.h>
#include <linux/kernel.h>
#include <linux/errno.h>
#include <linux/skbuff.h>
#include <linux/rtnetlink.h>

#include <net/netlink.h>
#include <net/pkt_sched.h>

/* debug support */
#define RRC_DEBUG   0
#define RRC_VERB    1
#define RRC_INFO    2
#define RRC_NOTHING 0xff
#define RRC_PRINT_LEVEL RRC_DEBUG

#define rrc_printk(l, f, arg...)                \
do {                                            \
    if (l >= RRC_PRINT_LEVEL) {                 \
        switch(l) {                             \
            case RRC_DEBUG:                     \
                printk(KERN_DEBUG f, ##arg);    \
                break;                          \
            case RRC_INFO:                      \
                printk(KERN_INFO f, ##arg);     \
                break;                          \
            default:                            \
                printk(KERN_NOTICE f, ##arg);    \
        }                                       \
    }                                           \
} while (0)
 
#define VERSION "0.1"

/*
     The simulator is limited by the Linux timer resolution
     and will create packet bursts on the HZ boundary (1ms).
*/

#define STATE_DCH            0x2
#define STATE_FACH            0x1
#define STATE_IDLE            0x0
#define STATE_TRANS            0x4
#define STATE_TRANS_DCH        (STATE_DCH | STATE_TRANS)
#define STATE_TRANS_FACH    (STATE_FACH | STATE_TRANS)

struct rrc_sched_data {
    struct Qdisc    *qdisc;
    struct qdisc_watchdog watchdog;

    u32    dch_tail;                /* length of dch tail in integral seconds */
    u32 fach_tail;                /* length of fach tail in integral seconds */
    u32    fach_dch_promo_mu;        /* average ms latency to upswitch from fach into dch */
    u32    fach_dch_promo_sigma;    /* +- ms latency to upswitch from fach into dch */
    u32 idle_promo_mu;            /* average ms latency to upswitch out of idle */
    u32 idle_promo_sigma;        /* +- ms latency to upswitch out of idle */
    u32 rlc_buf_threshold_ul;    /* RLC buffer threshold to leave fach for uplink */
    u32 rlc_buf_threshold_dl;    /* RLC buffer threholds to leave fach for downlink */
        u32 delay;                  /* Wireless channel delay (average ms) */
        u32 jitter;                 /* Wireless channel jitter (stdev ms) */
        u32 drop;                   /* Wireless channel % drop packets */
        u32 dl_dch_rate;            /* Wireless channel downlink rate in bps */
        u32 ul_dch_rate;            /* Wireless channel uplink rate in bps */
    u32    flags;
    /* Bunch of stats */
    u32 dch_pkts_ul;
    u32 dch_pkts_dl;
    u32 dch_bytes_ul;
    u32 dch_bytes_dl;
    u32 fach_pkts_ul;
    u32 fach_pkts_dl;
    u32 fach_bytes_ul;
    u32 fach_bytes_dl;
    u32 idle_upswitch;
    u32 dch_downswitch;
    u32 fach_upswitch;
    u32 fach_downswitch;
    u32 dch_ticks;
    u32 fach_ticks;
    u32 idle_trans_ticks;
    u32 fach_trans_ticks;
    u32 fd_calls;
    u32 fd_sleep_ticks;
    u32 fd_pkt_drops;
    u32 fd_byte_drops;

    /* The state machine */
    u8 state;
    psched_time_t dch_start;
    psched_time_t dch_end;
    psched_time_t fach_end;

    /* More timestamps, for stats */
    psched_time_t dch_t0;
    psched_time_t fach_t0;
    psched_time_t last_fd;

    /* How we emulate FACH. We enforce strict FIFO, one skb after the other, using the 
     * drainage equations from Qian et al, Mobisys 11, to calculate how long it will 
     * take the skb to leave the system in FACH mode. We also maintain current RLC
     * buffer occupancy to trigger upswitch into DCH. */ 
    psched_time_t    next_fach_ul_skb;
    psched_time_t    next_fach_dl_skb;
    u32 rlc_fach_ul_bytes;
    u32 rlc_fach_dl_bytes;

    /* So far, for DCH, we ensure FIFOness in the presence of variable delay */
    psched_time_t next_dch_ul_skb;
    psched_time_t next_dch_dl_skb;
};

/* Time stamp put into socket buffer control block */
struct rrc_skb_cb {
    /* TIme the skb will leave the queue */
    psched_time_t time_to_send;
    /* State with which the skb was enqueued */
    u8 state;
};

static inline struct rrc_skb_cb *rrc_skb_cb(struct sk_buff *skb)
{
        BUILD_BUG_ON(sizeof(skb->cb) <
                sizeof(struct qdisc_skb_cb) + sizeof(struct rrc_skb_cb));
        return (struct rrc_skb_cb *)qdisc_skb_cb(skb)->data;
}

/**** Handle flags ****/
/* upswitch from IDLE into DCH, otherwise IDLE->FACH */
static inline int idle_to_dch(struct rrc_sched_data *q) {
    return !!(q->flags & RRC_FLAG_IDLE_TO_DCH);
}

/* If operating on a vif from a Xen dom0, ingress is 
 * actually egress, and viceversa */
static inline int if_invert(struct rrc_sched_data *q) {
    return !!(q->flags & RRC_FLAG_IF_INVERT);
}

/**** Handle time ****/

static inline void copy_psched_time(psched_time_t *src, psched_time_t *dst) {
    (void)memcpy(dst, src, sizeof(*dst));
}

static inline unsigned long psched_time_to_ulong(const psched_time_t *_tv) {
    struct timeval *tv = (struct timeval *) _tv;
    return ((unsigned long) 
            ((((unsigned long) tv->tv_sec) * USEC_PER_SEC) + 
              ((unsigned long) tv->tv_usec)));
}

static inline psched_tdiff_t ms_to_psched_tdiff(unsigned long ms) {
    return ((psched_tdiff_t) (ms * 1000));
}

static inline unsigned long really_diff_psched(psched_time_t t0, psched_time_t t1) {
    return ((unsigned long) t1 - t0);
}

/* static inline unsigned long really_diff_psched(psched_time_t t0, psched_time_t t1) {
    return ((unsigned long) 
            ((t1.tv_usec - t0.tv_usec) + ((t1.tv_sec - t0.tv_sec) * USEC_PER_SEC))); 
}*/



static inline void reset_stats(struct rrc_sched_data *q) {
    q->dch_pkts_ul        = 0;
    q->dch_pkts_dl        = 0;
    q->dch_bytes_ul        = 0;
    q->dch_bytes_dl        = 0;
    q->fach_pkts_ul        = 0;
    q->fach_pkts_dl        = 0;
    q->fach_bytes_ul    = 0;
    q->fach_bytes_dl    = 0;
    q->idle_upswitch    = 0;
    q->dch_downswitch    = 0;
    q->fach_upswitch    = 0;
    q->fach_downswitch    = 0;
    q->dch_ticks        = 0;
    q->fach_ticks        = 0;
    q->idle_trans_ticks    = 0;
    q->fach_trans_ticks    = 0;
    q->fd_calls            = 0;
    q->fd_sleep_ticks    = 0;
    q->fd_pkt_drops        = 0;
    q->fd_byte_drops    = 0;
}

/* Entering/leaving DCH mode, reset all relevant counters and queues */
static inline void reset_dch(struct rrc_sched_data *q) {
    q->next_dch_ul_skb = PSCHED_PASTPERFECT;
    q->next_dch_dl_skb = PSCHED_PASTPERFECT;
}

/* Entering/leaving FACH mode, reset all relevant counters and queues */
static inline void reset_fach(struct rrc_sched_data *q) {
    q->rlc_fach_ul_bytes = q->rlc_fach_dl_bytes = 0;
    q->next_fach_ul_skb = PSCHED_PASTPERFECT;
    q->next_fach_dl_skb = PSCHED_PASTPERFECT;
}

/* Take care of the packets still enqueued in the FACH state */
static inline void enqueue_dch(struct rrc_sched_data *q, struct sk_buff *skb, u32 from);

static inline void upswitch_fach_to_dch(struct rrc_sched_data *q, psched_time_t *when) {
    struct sk_buff_head temp_list;
    skb_queue_head_init(&temp_list);

    if ((q->rlc_fach_ul_bytes + q->rlc_fach_dl_bytes) == 0) {
        rrc_printk(RRC_DEBUG, "Free upswitch FACH to DCH qlen is %u\n", 
                    skb_queue_len(&(q->qdisc->q)));
        return;
    }

    /* Move packets out of FACH queues into a temp queue. Update time of transmission 
     * to when. There should not be anything non-fach in the queue */
    while (skb_queue_len(&(q->qdisc->q))) {
        struct rrc_skb_cb *cb;
        psched_time_t *skb_t;
        u32 from;
        struct sk_buff *skb = q->qdisc->dequeue(q->qdisc);

        if (!skb) {
            rrc_printk(RRC_VERB, "GAAAA skb queue non-empty yet dequeueing yield NULL skb\n");
            break;
        }
        q->qdisc->bstats.bytes -= qdisc_pkt_len(skb);
        q->qdisc->bstats.packets--;
        cb       = rrc_skb_cb(skb);
        skb_t = &(cb->time_to_send);
        from = G_TC_FROM(skb->tc_verd);

        if (!(cb->state & STATE_FACH)) {
            rrc_printk(RRC_DEBUG, "GAAAA skb %p len %u state %x time %lu dequeued while upswitching "
                    "FACH to DCH\n", skb, skb->len, cb->state, psched_time_to_ulong(skb_t));
        }
        rrc_printk(RRC_DEBUG, "Former FACH packet with time %lu state %x will now be sent at time %lu "
                "state %x\n", psched_time_to_ulong(skb_t), cb->state,
                psched_time_to_ulong(when), (q->state & (~STATE_TRANS)));

        copy_psched_time(when, skb_t);
        enqueue_dch(q, skb, from);
        __skb_queue_tail(&temp_list, skb);
        if (from & ((if_invert(q)) ? AT_INGRESS : AT_EGRESS)) {
            q->rlc_fach_ul_bytes -= qdisc_pkt_len(skb);
        } else {
            q->rlc_fach_dl_bytes -= qdisc_pkt_len(skb);
        }
    }

    /* Make sure no more bytes are left in FACH */
    if ((q->rlc_fach_ul_bytes + q->rlc_fach_dl_bytes) != 0) {
        rrc_printk(RRC_VERB, "GAA upswitch FACH to DCH left bytes UL %u DL %u qlen is %u\n", 
                q->rlc_fach_ul_bytes, q->rlc_fach_dl_bytes, 
                skb_queue_len(&(q->qdisc->q)));
    }

    /* Queue stuff back into the general queue, respecting order */
    while (skb_queue_len(&temp_list)) {
        struct sk_buff *skb = __skb_dequeue(&temp_list);
        int ret;

        if (!skb) {
            rrc_printk(RRC_VERB, "GAAAA skb temp queue non-empty yet dequeueing yield NULL skb\n");
            break;
        }

        ret = q->qdisc->enqueue(skb, q->qdisc);
        if (ret != NET_XMIT_SUCCESS) {
            struct rrc_skb_cb *cb       = rrc_skb_cb(skb);
            rrc_printk(RRC_VERB, "GAAA failure to requeue skb %p len %u state %x time %lu from "
                    "temp queue\n",    skb, skb->len, cb->state, 
                    psched_time_to_ulong(&(cb->time_to_send)));
        }
    }

    /* Reset FACH state for good measure */
    reset_fach(q);
}

/**** State machine manipulation ****/
static inline void update_tails(struct rrc_sched_data *q) {
    if (q->state & STATE_DCH) {
        /* Assumes dch_start initialized */
        q->dch_end = q->dch_start + (psched_tdiff_t) q->dch_tail;
    }
    q->dch_end = q->dch_end + (psched_tdiff_t) q->dch_tail;
}

static inline void update_timers(struct rrc_sched_data *q) {
    if (q->state & STATE_DCH) {
        q->dch_start = psched_get_time();
    } else {
        q->dch_end = psched_get_time();
    }
    update_tails(q);
}

/* Uniformly distributed random number generator */
static inline unsigned long get_random_uniform(unsigned long mu, long sigma)
{
    if (!sigma) return mu;
    if (sigma > mu) sigma = mu;
    return (((unsigned long) net_random()) % (2*sigma)) - sigma + mu;
}

/* When the state machine enters an active state (FACH, DCH), queues
 * may need to be cleared, deadlines recalculated and tails updated.
 * On input now is now, on output, now is when the next transmission
 * will be feasible. */
static inline void transition_state(struct rrc_sched_data *q, psched_time_t *now) {
    psched_tdiff_t delay;
    int upswitch = 0;

    /* We only transition out of IDLE or FACH */
    if (q->state & STATE_DCH) {
        rrc_printk(RRC_DEBUG, "ERROR RRC transition routine called already in state %x\n", q->state);
        return;
    }

    if (q->state == STATE_IDLE) {
        delay = (psched_tdiff_t) 
                    get_random_uniform(q->idle_promo_mu, q->idle_promo_sigma);
        q->state = STATE_TRANS;
        q->state |= (idle_to_dch(q)) ? STATE_DCH : STATE_FACH;
        q->idle_upswitch++;
        q->idle_trans_ticks += delay;
        /* Handle sleep from fast dormancy */
        if (!(q->last_fd == PSCHED_PASTPERFECT)) {
            q->fd_sleep_ticks += ((u32) really_diff_psched(q->last_fd, *now));
            q->last_fd = PSCHED_PASTPERFECT;
        }
    } else {
        /* The only other choice is being in FACH to DCH */
        delay = (psched_tdiff_t)
                    get_random_uniform(q->fach_dch_promo_mu, q->fach_dch_promo_sigma);
        q->state = STATE_TRANS_DCH;
        upswitch = 1;
        q->fach_upswitch++;
        q->fach_trans_ticks += delay;
        q->fach_ticks += ((u32) really_diff_psched(q->fach_t0, *now));
    }

    if (q->state & STATE_DCH) {
        rrc_printk(RRC_VERB, "Transition to DCH with delay %lu\n", (unsigned long) delay);
        q->dch_start = *now + (psched_tdiff_t) delay;
        copy_psched_time(&(q->dch_start), now);
        copy_psched_time(&(q->dch_start), &(q->dch_t0));
        reset_dch(q);
        if (upswitch) upswitch_fach_to_dch(q, now);
    } else {
        rrc_printk(RRC_VERB, "Transition to FACH with delay %lu\n", (unsigned long) delay);
        q->dch_end = *now + (psched_tdiff_t) delay;
        copy_psched_time(&(q->dch_end), now);
        copy_psched_time(&(q->dch_end), &(q->fach_t0));
        reset_fach(q);
    }

    rrc_printk(RRC_DEBUG, " -- skb still has to wait until usecs %lu\n", psched_time_to_ulong(now));
    update_tails(q);
}

/* Updates the state machine and stores in the arg-by-val the time spec for 
 * when this packet can hit the wire. The stats flag only exists for the 
 * purpose of user-space consultation: states have to be updated for 
 * accounting only -- introduces some icky corner-cases, sigh.... */
static inline void update_state(struct rrc_sched_data *q, psched_time_t *now, int stats) {
    psched_time_t *deadline;

    *now = psched_get_time();
    rrc_printk(RRC_DEBUG, "NOW is %lu", psched_time_to_ulong(now));

    if (stats) {
        rrc_printk(RRC_DEBUG, " -- Stats gather");
        goto state_machine_test_tail;
    }

state_machine_is_idle:
    /* Are we in IDLE? */
    if (q->state == STATE_IDLE) {
        transition_state(q, now); 
        return;
    }

    if (q->state & STATE_TRANS) {
        /* The state machine is transitioning */
        deadline = (q->state & STATE_DCH) ? &(q->dch_start) : &(q->dch_end);
        if (!(*deadline >= *now)) {
            /* The deadline has passed, and the state machine is done transitioning */
            q->state &= ~STATE_TRANS;
            rrc_printk(RRC_DEBUG, " -- done transitioning");
        } else {
            copy_psched_time(deadline, now);
            rrc_printk(RRC_DEBUG, " -- skb still has to wait until usecs %lu\n", psched_time_to_ulong(now));
            return;
        }
    }

state_machine_test_tail:
    /* Figure out our next tail */
    deadline = (q->state & STATE_DCH) ? &(q->dch_end) : &(q->fach_end);
    if (!(*deadline >= *now)) {
        /* Whoops, tail has passed */
        if (q->state & STATE_DCH) {
            q->state = STATE_FACH;
            rrc_printk(RRC_DEBUG, " -- dropped of DCH");
            q->dch_downswitch++;
            q->dch_ticks += ((u32) really_diff_psched(q->dch_t0, q->dch_end));
            copy_psched_time(&(q->dch_end), &(q->fach_t0));
            reset_dch(q);
            reset_fach(q);
            goto state_machine_test_tail;
        } else {
            if (stats && (q->state == STATE_IDLE)) {
                /* Icky corner case */
                rrc_printk(RRC_DEBUG, "\n"); return;
            }
            /* FACH tail, we go IDLE */
            q->state = STATE_IDLE;
            rrc_printk(RRC_DEBUG, " -- dropped of FACH");
            q->fach_downswitch++;
            q->fach_ticks += ((u32) really_diff_psched(q->fach_t0, q->fach_end));
            reset_fach(q);
            if (!stats) goto state_machine_is_idle;
        }
    }

    if (stats) {
        rrc_printk(RRC_DEBUG, "\n");
    } else {
        rrc_printk(RRC_DEBUG, " -- skb will transmit now at usecs %lu\n", psched_time_to_ulong(now));
        update_timers(q);
    }
    return;
}

/* Stats, reset timers, drop all packets */
static inline void do_fast_dormancy(struct Qdisc *sch) {
    struct rrc_sched_data *q = qdisc_priv(sch);

    rrc_printk(RRC_INFO, "FAST DORMANCY dropping %d packets", skb_queue_len(&(q->qdisc->q)));
    q->fd_calls++;

    /* Drop packets */
    while (skb_queue_len(&(q->qdisc->q))) {
        struct sk_buff *skb = q->qdisc->dequeue(q->qdisc);
        if (!skb) {
            rrc_printk(RRC_DEBUG, " -- ODD dequeque fail yet queue_len non zero");
            break;
        }
        sch->qstats.drops++;
        q->fd_pkt_drops++;
        q->fd_byte_drops += qdisc_pkt_len(skb);
        kfree_skb(skb);
    }
    rrc_printk(RRC_INFO, "\n");

    /* Update stats */
    update_state(q, &(q->last_fd), 1);
    if (q->state & STATE_DCH) {
        q->dch_ticks += ((u32) really_diff_psched(q->dch_t0, q->last_fd));
    } else {
        if (q->state & STATE_FACH) {
            q->fach_ticks += ((u32) really_diff_psched(q->fach_t0, q->last_fd));
        }
    }
    reset_fach(q);
    reset_dch(q);
    q->state = STATE_IDLE;
}

static inline void cap_delay(struct rrc_sched_data *q, psched_time_t *now, 
                                psched_time_t *next_skb, psched_tdiff_t prop_delay)
{
    /* Algo works as follows:
     * -now contains the first available time to send, which is already
     *  set to the end of the transition if necessary
     * -delay is the end-to-end delay (ping) in the wireless channel
     * -prop_delay is packet_size / channel_rate
     *
     * The channel is exclusively FIFO, hence next_skb. Even in the
     * presence of jitter, no packet can come out of order.
     *
     * Finally, no two packets can come closer than the prop_delay,
     * which enforces the rate on the channel
     */
     psched_tdiff_t delay;
    if (q->delay) {
         delay = (psched_tdiff_t) 
                                get_random_uniform(q->delay, q->jitter);
        *now += delay;
    }
    if (*next_skb == PSCHED_PASTPERFECT) {
        /* This skb is the first for this period. Easy peasy */
        *now += prop_delay;
    } else {
        /* There is a previous skb sent in this queue. Figure out
         * if it's done or we need to wait */
        if (!(*next_skb >= *now)) {
            /* Done, we can send now */
            *now += prop_delay;
        } else {
            /* Not done, we send after it finishes */
            *now = *next_skb + prop_delay;
        }
    }

    /* Next skb after us will only be able to transmit after we're done */
    copy_psched_time(now, next_skb);
}

/* How to send a packet in FACH state. */
static inline void enqueue_fach(struct rrc_sched_data *q, 
                                struct sk_buff *skb, u32 from) {
    /* For FACH, first figure out direction (u32 from), and see if adding 
     * skb->len causes buffer overflow and therefore switch to DCH.
     *
     * Otherwise, calculate ETA for transmission finish based on
     * 1. direction (u32 from)
     * 2. start, max(cb->time_to_send, fach_dl/ul queue last finish)
     * 3. equations from Feng Qian Mobisys 2011.
     * And store the skb with updated time_to_send.
     *
     * Should an upswitch to DCH happen, all queued packets will be 
     * moved into DCH state */
    struct rrc_skb_cb *cb       = rrc_skb_cb(skb);
    psched_time_t *now      = &(cb->time_to_send);
    int go_to_dch           = 0;
    psched_time_t *next_skb;
    unsigned long prop_delay;

    if (!(q->state & STATE_FACH)) {
        rrc_printk(RRC_DEBUG, "Asked to send a packet as FACH but state is %x\n", q->state);
        return;
    }

    if (from & ((if_invert(q)) ? AT_INGRESS : AT_EGRESS)) {
        q->rlc_fach_ul_bytes += qdisc_pkt_len(skb);
        if (q->rlc_fach_ul_bytes > q->rlc_buf_threshold_ul) {
            rrc_printk(RRC_INFO, "SKB %p EGRESS %u bumping FACH (%x) UL threshold past "
                    "limit (%u:%u)\n", skb, qdisc_pkt_len(skb), q->state, 
                    q->rlc_fach_ul_bytes, q->rlc_buf_threshold_ul);
            q->rlc_fach_ul_bytes -= qdisc_pkt_len(skb);
            go_to_dch = 1;
        }
    } else {
        q->rlc_fach_dl_bytes += qdisc_pkt_len(skb);
        if (q->rlc_fach_dl_bytes > q->rlc_buf_threshold_dl) {
            rrc_printk(RRC_INFO, "SKB %p INGRESS %u bumping FACH (%x) DL threshold past "
                    "limit (%u:%u)\n", skb, qdisc_pkt_len(skb), q->state, 
                    q->rlc_fach_dl_bytes, q->rlc_buf_threshold_dl);
            q->rlc_fach_dl_bytes -= qdisc_pkt_len(skb);
            go_to_dch = 1;
        }
    }

    if (go_to_dch) {
        cb->time_to_send = psched_get_time();
        rrc_printk(RRC_DEBUG, "SKB moving FACH to DCH at time %lu", psched_time_to_ulong(&(cb->time_to_send)));
        transition_state(q, &(cb->time_to_send));
        enqueue_dch(q, skb, from);
        return;
    }

    /* Ok no overflows, regular transmittal */
    if (from & ((if_invert(q)) ? AT_INGRESS : AT_EGRESS)) {
        prop_delay = ((unsigned long) ((0.0014 * ((float) (skb->len * skb->len))) +
                (1.6 * ((float) skb->len)) + 20.0));
        next_skb = &(q->next_fach_ul_skb);
    } else {
        prop_delay = ((unsigned long) ((0.1 * ((float) skb->len)) + 10.0));
        next_skb = &(q->next_fach_dl_skb);
    }

    /* Calculate when we'll be done sending */
    cap_delay(q, now, next_skb, ms_to_psched_tdiff(prop_delay));
    rrc_printk(RRC_VERB, "FACH transmittal of skb %p len %u %s scheduled at time %lu\n", skb, skb->len, 
            (from & ((if_invert(q)) ? AT_INGRESS : AT_EGRESS)) ? "EGRESS" : "INGRESS",
            psched_time_to_ulong(now));
    cb->state = STATE_FACH;
}
    
/* In DCH mode, we add delay, jitter, and shaping, still undecided how */
static inline void enqueue_dch(struct rrc_sched_data *q, struct sk_buff *skb, u32 from) {
    psched_time_t *next_skb;
    struct rrc_skb_cb *cb       = rrc_skb_cb(skb);
    psched_time_t *now        = &(cb->time_to_send);
    unsigned long prop_delay; /* In ms. Rates are passed down in bytes per sec */
    
    if (from & ((if_invert(q)) ? AT_INGRESS : AT_EGRESS)) {
        next_skb = &(q->next_dch_ul_skb);
        prop_delay = (skb->len * 1000) / q->ul_dch_rate;
    } else {
        next_skb = &(q->next_dch_dl_skb);
        prop_delay = (skb->len * 1000) / q->dl_dch_rate;
    }

    /* Calculate when we'll be done sending */
    cap_delay(q, now, next_skb, ms_to_psched_tdiff(prop_delay));
    rrc_printk(RRC_VERB, "DCH transmittal of skb %p len %u %s scheduled at time %lu\n", skb, skb->len, 
            (from & ((if_invert(q)) ? AT_INGRESS : AT_EGRESS)) ? "EGRESS" : "INGRESS",
            psched_time_to_ulong(now));
    cb->state = STATE_DCH;
}

/*
 * Insert one skb into qdisc.
 * Note: parent depends on return value to account for queue length.
 *     NET_XMIT_DROP: queue length didn't change.
 *  NET_XMIT_SUCCESS: one skb was queued.
 */
static int rrc_enqueue(struct sk_buff *skb, struct Qdisc *sch)
{
    struct rrc_sched_data *q    = qdisc_priv(sch);
    struct rrc_skb_cb *cb       = rrc_skb_cb(skb);
    u32 from                    = G_TC_FROM(skb->tc_verd);
    int ret;

    pr_debug("rrc_enqueue skb=%p\n", skb);

    /* We don't like skb's we don't know where they're coming from */
    if ((!(from & AT_INGRESS)) && (!(from & AT_EGRESS))) {
        rrc_printk(RRC_DEBUG, "skb %p len %u unknown direction\n", skb, skb->len);
        sch->qstats.drops++;
        kfree_skb(skb);
        return NET_XMIT_DROP;
    }
    cb->state = 0;

    /* Kick the state machine. Time to send this packet will be 
     * stored in callback */
    update_state(q, &(cb->time_to_send), 0);

    /* Do we drop */
    if ((q->drop) && (q->drop >= net_random())) {
        rrc_printk(RRC_INFO, "skb %p len %u DROP\n", skb, skb->len);
        sch->qstats.drops++;
        kfree_skb(skb);
        return NET_XMIT_SUCCESS | __NET_XMIT_BYPASS;
    }

    /* At this point we know state and when transmission will initiate. */
    if (q->state & STATE_FACH) {
        enqueue_fach(q, skb, from);
    } else {
        /* State is never IDLE after update state */
        enqueue_dch(q, skb, from);
    }

    ret = q->qdisc->enqueue(skb, q->qdisc);

    if (likely(ret == NET_XMIT_SUCCESS)) {
        sch->q.qlen++;
    } else if (net_xmit_drop_count(ret)) {
        sch->qstats.drops++;
    }

    pr_debug("rrc: enqueue ret %d\n", ret);
    return ret;
}

static unsigned int rrc_drop(struct Qdisc* sch)
{
    struct rrc_sched_data *q = qdisc_priv(sch);
    unsigned int len = 0;

    if (q->qdisc->ops->drop && (len = q->qdisc->ops->drop(q->qdisc)) != 0) {
        sch->q.qlen--;
        sch->qstats.drops++;
    }
    return len;
}

static struct sk_buff *rrc_dequeue(struct Qdisc *sch)
{
    struct rrc_sched_data *q = qdisc_priv(sch);
    struct sk_buff *skb;

     if (sch->flags & TCQ_F_THROTTLED)
                 return NULL;
 
    skb = q->qdisc->ops->peek(q->qdisc);
    if (skb) {
        const struct rrc_skb_cb *cb = rrc_skb_cb(skb);
        psched_time_t now = psched_get_time();

        if (cb->time_to_send >= now) {
            u32 from = G_TC_FROM(skb->tc_verd);
            skb = qdisc_dequeue_peeked(q->qdisc);
            if (unlikely(!skb))
                                return NULL;

            if (from & ((if_invert(q)) ? AT_INGRESS : AT_EGRESS)) {
                rrc_printk(RRC_DEBUG, "SKB %p EGRESS %u", skb, skb->len);
                if (q->state & STATE_FACH) {
                    q->rlc_fach_ul_bytes -= qdisc_pkt_len(skb);
                    rrc_printk(RRC_DEBUG, " -- RLC FACH UL now at %u", q->rlc_fach_ul_bytes);
                    q->fach_pkts_ul++;
                    q->fach_bytes_ul += qdisc_pkt_len(skb);
                } else {
                    q->dch_pkts_ul++;
                    q->dch_bytes_ul += qdisc_pkt_len(skb);
                }
            } else {
                rrc_printk(RRC_DEBUG, "SKB %p INGRESS %u", skb, skb->len);
                if (q->state & STATE_FACH) {
                    q->rlc_fach_dl_bytes -= qdisc_pkt_len(skb);
                    rrc_printk(RRC_DEBUG, " -- RLC FACH DL now at %u", q->rlc_fach_dl_bytes);
                    q->fach_pkts_dl++;
                    q->fach_bytes_dl += qdisc_pkt_len(skb);
                } else {
                    q->dch_pkts_dl++;
                    q->dch_bytes_dl += qdisc_pkt_len(skb);
                }
            }
            rrc_printk(RRC_DEBUG, "\n");

            pr_debug("rrc_dequeue: return skb=%p\n", skb);
                        sch->q.qlen--;
            return skb;
            }
    
            qdisc_watchdog_schedule(&q->watchdog, cb->time_to_send);
    }

    return NULL;
}

static void rrc_reset(struct Qdisc *sch)
{
    struct rrc_sched_data *q = qdisc_priv(sch);

    qdisc_reset(q->qdisc);
    sch->q.qlen = 0;
    qdisc_watchdog_cancel(&q->watchdog);
}

/* Parse netlink message to set options */
static int rrc_change(struct Qdisc *sch, struct nlattr *opt)
{
    struct rrc_sched_data *q = qdisc_priv(sch);
    struct tc_rrc_qopt *qopt;
    
    if (opt == NULL)
                return -EINVAL;

    qopt = nla_data(opt);
    /* Handle fast dormancy independently */
    if (qopt->flags & RRC_FLAG_FAST_DORMANCY) {
        do_fast_dormancy(sch);
        return 0;
    }
    
    q->dch_tail                 = qopt->dch_tail;
    q->fach_tail                = qopt->fach_tail;
    q->fach_dch_promo_mu        = qopt->fach_dch_promo_mu;
    q->fach_dch_promo_sigma     = qopt->fach_dch_promo_sigma;
    q->idle_promo_mu            = qopt->idle_promo_mu;
    q->idle_promo_sigma         = qopt->idle_promo_sigma;
    q->rlc_buf_threshold_ul     = qopt->rlc_buf_threshold_ul;
    q->rlc_buf_threshold_dl     = qopt->rlc_buf_threshold_dl;
    q->delay                    = qopt->delay;
    q->jitter                   = qopt->jitter;
    q->drop                     = qopt->drop;
    q->dl_dch_rate              = qopt->dl_dch_rate;
    q->ul_dch_rate              = qopt->ul_dch_rate;
    q->flags                    = qopt->flags;

    rrc_printk(RRC_INFO, "Updating RRC queueing module for dev %s: DCH Tail %u FACH Tail %u FACH->DCH %u +- %u IDLE->%s %u +- %u RLC UL %u DL %u %s"
            " DELAY %u JITTER %u DROP pct %u DCH RATE UL %u DL %u\n",
            qdisc_dev(sch)->name, q->dch_tail, q->fach_tail, q->fach_dch_promo_mu, q->fach_dch_promo_sigma, (idle_to_dch(q)) ? "DCH" : "FACH",
            q->idle_promo_mu, q->idle_promo_sigma, q->rlc_buf_threshold_ul, q->rlc_buf_threshold_dl, (if_invert(q)) ? "INVERTED" : " ",
            q->delay, q->jitter, q->drop, q->ul_dch_rate, q->dl_dch_rate);

    return 0;
}

/*
 * Special case version of FIFO queue for use by rrc.
 * It queues in order based on timestamps in skb's
 */
struct rrcfifo_sched_data {
    u32 limit;
    psched_time_t oldest;
};

static int rrcfifo_enqueue(struct sk_buff *nskb, struct Qdisc *sch)
{
    struct rrcfifo_sched_data *q = qdisc_priv(sch);
    struct sk_buff_head *list = &sch->q;
    psched_time_t tnext = rrc_skb_cb(nskb)->time_to_send;
    struct sk_buff *skb;

    if (likely(skb_queue_len(list) < q->limit)) {
                /* Optimize for add at tail */
                if (likely(skb_queue_empty(list) || tnext >= q->oldest)) {
                        q->oldest = tnext;
                        return qdisc_enqueue_tail(nskb, sch);
                }

                skb_queue_reverse_walk(list, skb) {
                        const struct rrc_skb_cb *cb = rrc_skb_cb(skb);

                        if (tnext >= cb->time_to_send)
                                break;
                }

                __skb_queue_after(list, skb, nskb);

                sch->qstats.backlog += qdisc_pkt_len(nskb);

                return NET_XMIT_SUCCESS;
        }

        return qdisc_reshape_fail(nskb, sch);

}

static int rrcfifo_init(struct Qdisc *sch, struct nlattr *opt)
{
    struct rrcfifo_sched_data *q = qdisc_priv(sch);

    if (opt) {
        struct tc_fifo_qopt *ctl = nla_data(opt);
        if (nla_len(opt) < sizeof(*ctl))
            return -EINVAL;
        if (ctl->limit > 0)
            q->limit = ctl->limit;
    } else
        q->limit = max_t(u32, qdisc_dev(sch)->tx_queue_len, 1);

    q->oldest = PSCHED_PASTPERFECT;

    return 0;
}

static int rrcfifo_dump(struct Qdisc *sch, struct sk_buff *skb)
{
    struct rrcfifo_sched_data *q = qdisc_priv(sch);
    struct tc_fifo_qopt opt = { .limit = q->limit };

    NLA_PUT(skb, TCA_OPTIONS, sizeof(opt), &opt);
    return skb->len;

nla_put_failure:
    return -1;
}

static struct Qdisc_ops rrcfifo_qdisc_ops __read_mostly = {
    .id            =    "rrcfifo",
    .priv_size    =    sizeof(struct rrcfifo_sched_data),
    .enqueue    =    rrcfifo_enqueue,
    .dequeue    =    qdisc_dequeue_head,
    .peek        =    qdisc_peek_head,
    .drop        =    qdisc_queue_drop,
    .init        =    rrcfifo_init,
    .reset        =    qdisc_reset_queue,
    .change        =    rrcfifo_init,
    .dump        =    rrcfifo_dump,
};

static int rrc_init(struct Qdisc *sch, struct nlattr *opt)
{
    struct rrc_sched_data *q = qdisc_priv(sch);
    int ret;

    if (!opt)
        return -EINVAL;

    qdisc_watchdog_init(&q->watchdog, sch);
    q->qdisc = qdisc_create_dflt(sch->dev_queue, 
                     &rrcfifo_qdisc_ops,
                                     TC_H_MAKE(sch->handle, 1));
    if (!q->qdisc) {
        pr_debug("rrc: qdisc of embedded fifo create failed\n");
        return -ENOMEM;
    }

    ret = rrc_change(sch, opt);
    if (ret) {
        pr_debug("rrc: change failed\n");
        qdisc_destroy(q->qdisc);
    } else {
        reset_stats(q);
        q->state = STATE_DCH;
        update_timers(q);
        copy_psched_time(&(q->dch_start), &(q->dch_t0));
    }

    return ret;
}

static void rrc_destroy(struct Qdisc *sch)
{
    struct rrc_sched_data *q = qdisc_priv(sch);

    qdisc_watchdog_cancel(&q->watchdog);
    qdisc_destroy(q->qdisc);
}

static int rrc_dump(struct Qdisc *sch, struct sk_buff *skb)
{
    struct rrc_sched_data *q = qdisc_priv(sch);
        unsigned char *b = skb_tail_pointer(skb);
        struct nlattr *nla = (struct nlattr *) b;
    struct tc_rrc_qopt qopt;
    psched_time_t now;

    qopt.dch_tail                 = q->dch_tail;
    qopt.fach_tail                = q->fach_tail;
    qopt.fach_dch_promo_mu        = q->fach_dch_promo_mu;
    qopt.fach_dch_promo_sigma     = q->fach_dch_promo_sigma;
    qopt.idle_promo_mu            = q->idle_promo_mu;
    qopt.idle_promo_sigma         = q->idle_promo_sigma;
    qopt.rlc_buf_threshold_ul     = q->rlc_buf_threshold_ul;
    qopt.rlc_buf_threshold_dl     = q->rlc_buf_threshold_dl;
    qopt.delay                    = q->delay;
    qopt.jitter                   = q->jitter;
    qopt.drop                     = q->drop;
    qopt.dl_dch_rate              = q->dl_dch_rate;
    qopt.ul_dch_rate              = q->ul_dch_rate;
    qopt.flags                    = q->flags;
    /* Stats too */
    update_state(q, &now, 1);
    qopt.dch_pkts_ul              = q->dch_pkts_ul;
    qopt.dch_pkts_dl              = q->dch_pkts_dl; 
    qopt.dch_bytes_ul             = q->dch_bytes_ul;
    qopt.dch_bytes_dl             = q->dch_bytes_dl;
    qopt.fach_pkts_ul             = q->fach_pkts_ul;
    qopt.fach_pkts_dl             = q->fach_pkts_dl;
    qopt.fach_bytes_ul            = q->fach_bytes_ul;
    qopt.fach_bytes_dl            = q->fach_bytes_dl;
    qopt.idle_upswitch            = q->idle_upswitch;
    qopt.dch_downswitch           = q->dch_downswitch;
    qopt.fach_upswitch            = q->fach_upswitch;
    qopt.fach_downswitch          = q->fach_downswitch;
    qopt.dch_ticks                = q->dch_ticks;
    qopt.fach_ticks               = q->fach_ticks;
    qopt.idle_trans_ticks         = q->idle_trans_ticks;
    qopt.fach_trans_ticks         = q->fach_trans_ticks;
    qopt.fd_calls                 = q->fd_calls;
    qopt.fd_sleep_ticks           = q->fd_sleep_ticks;
    qopt.fd_pkt_drops             = q->fd_pkt_drops;
    qopt.fd_byte_drops            = q->fd_byte_drops;

    NLA_PUT(skb, TCA_OPTIONS, sizeof(qopt), &qopt);

        nla->nla_len = skb_tail_pointer(skb) - b;

        return skb->len;

nla_put_failure:
        nlmsg_trim(skb, b);
        return -1;
}

/** Class operations, very generic **/

static int rrc_dump_class(struct Qdisc *sch, unsigned long cl,
              struct sk_buff *skb, struct tcmsg *tcm)
{
    struct rrc_sched_data *q = qdisc_priv(sch);

    if (cl != 1)     /* only one class */
        return -ENOENT;

    tcm->tcm_handle |= TC_H_MIN(1);
    tcm->tcm_info = q->qdisc->handle;

    return 0;
}

static int rrc_graft(struct Qdisc *sch, unsigned long arg, struct Qdisc *new,
             struct Qdisc **old)
{
    struct rrc_sched_data *q = qdisc_priv(sch);

    if (new == NULL)
        new = &noop_qdisc;


        sch_tree_lock(sch);
        *old = q->qdisc;
        q->qdisc = new;
        qdisc_tree_decrease_qlen(*old, (*old)->q.qlen);
        qdisc_reset(*old);
        sch_tree_unlock(sch);
        return 0;
}

static struct Qdisc *rrc_leaf(struct Qdisc *sch, unsigned long arg)
{
    struct rrc_sched_data *q = qdisc_priv(sch);
    return q->qdisc;
}

static unsigned long rrc_get(struct Qdisc *sch, u32 classid)
{
    return 1;
}

static void rrc_put(struct Qdisc *sch, unsigned long arg)
{
}

static int rrc_change_class(struct Qdisc *sch, u32 classid, u32 parentid, 
                struct nlattr **tca, unsigned long *arg)
{
    return -ENOSYS;
}

static int rrc_delete(struct Qdisc *sch, unsigned long arg)
{
    return -ENOSYS;
}

static void rrc_walk(struct Qdisc *sch, struct qdisc_walker *walker)
{
    if (!walker->stop) {
        if (walker->count >= walker->skip)
            if (walker->fn(sch, 1, walker) < 0) {
                walker->stop = 1;
                return;
            }
        walker->count++;
    }
}

static struct tcf_proto **rrc_find_tcf(struct Qdisc *sch, unsigned long cl)
{
    return NULL;
}

static struct Qdisc_class_ops rrc_class_ops = {
    .graft        =    rrc_graft,
    .leaf        =    rrc_leaf,
    .get        =    rrc_get,
    .put        =    rrc_put,
    .change        =    rrc_change_class,
    .delete        =    rrc_delete,
    .walk        =    rrc_walk,
    .tcf_chain    =    rrc_find_tcf,
    .dump        =    rrc_dump_class,
};

/** Module initialization **/

static struct Qdisc_ops rrc_qdisc_ops __read_mostly = {
    .id            =    "rrc",
    .cl_ops        =    &rrc_class_ops,
    .priv_size    =    sizeof(struct rrc_sched_data),
    .enqueue    =    rrc_enqueue,
    .dequeue    =    rrc_dequeue,
    .peek           =       qdisc_peek_dequeued,
    .drop        =    rrc_drop,
    .init        =    rrc_init,
    .reset        =    rrc_reset,
    .destroy    =    rrc_destroy,
    .change        =    rrc_change,
    .dump        =    rrc_dump,
    .owner        =    THIS_MODULE,
};


static int __init rrc_module_init(void)
{
    pr_info("rrc: version " VERSION "\n");
    return register_qdisc(&rrc_qdisc_ops);
}
static void __exit rrc_module_exit(void)
{
    unregister_qdisc(&rrc_qdisc_ops);
}
module_init(rrc_module_init)
module_exit(rrc_module_exit)
MODULE_LICENSE("GPL");

---

