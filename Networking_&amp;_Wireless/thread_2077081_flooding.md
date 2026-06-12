---
title: "flooding"
date: 2012-10-27
forum: Networking &amp; Wireless
---

### Post by mycy on 2012-10-27
hello everyone i am working on contiki and i have a unicast-flooding code but i have no idea how it works.. i've noticed that after few seconds the sink node doesn't receive any packets from some nodes.. how is this happening?

here is the code can somebody please help me?

thnx

#include "contiki.h"
#include "net/rime.h"

#include "dev/button-sensor.h"

#include "dev/leds.h"

#include <stdio.h>

#define FLOODING_COEF 0.1

/*---------------------------------------------------------------------------*/
PROCESS(example_unicast_process, "Example unicast");
AUTOSTART_PROCESSES(&example_unicast_process);
/*---------------------------------------------------------------------------*/
static void
recv_uc(struct unicast_conn *c, const rimeaddr_t *from)
{
  printf("unicast message received from %d.%d\n",
         from->u8[0], from->u8[1]);
}
static const struct unicast_callbacks unicast_callbacks = {recv_uc};
static struct unicast_conn uc;
/*---------------------------------------------------------------------------*/
PROCESS_THREAD(example_unicast_process, ev, data)
{
  PROCESS_EXITHANDLER(unicast_close(&uc);)
    
  PROCESS_BEGIN();

  unicast_open(&uc, 146, &unicast_callbacks);

  static int i = 0;

  while(1) {
    static struct etimer et;
    rimeaddr_t addr;
    
    etimer_set(&et, CLOCK_SECOND * FLOODING_COEF);
    
    PROCESS_WAIT_EVENT_UNTIL(etimer_expired(&et));

    packetbuf_copyfrom("Flooding", 8);
    addr.u8[0] = 1;
    addr.u8[1] = 0;
    if(!rimeaddr_cmp(&addr, &rimeaddr_node_addr)) {
      unicast_send(&uc, &addr);
		i++;
		printf("Packet #%d sent\n", i);
    }

  }

  PROCESS_END();
}

---

