# BRACKEN DNS

**DNS services and health-aware traffic steering for BRACKEN.**

BRACKEN DNS is intended to provide DNS capabilities for BRACKEN deployments, including recursive resolution, authoritative service, caching, DNSSEC support, health-aware responses, and operational visibility. These capabilities may be delivered through integrations with established DNS software and BRACKEN-specific management components.

> **Project status:** Early-stage project. Resolver and authoritative implementations, protocol coverage, and service-level objectives are not yet selected.

## Responsibilities

- Define service boundaries for recursive and authoritative DNS.
- Manage zones, records, and configuration through validated interfaces.
- Provide caching and operational controls appropriate to each DNS role.
- Plan DNSSEC validation and signing workflows.
- Support health-aware answers and traffic steering where the deployment model allows.
- Export query, latency, cache, and error statistics for observability.

## Scope boundaries

DNS answers can influence where clients connect, but DNS alone does not guarantee delivery or global traffic distribution. The [control plane](https://github.com/vayun-networks/bracken-control-plane) should own configuration orchestration; [observability](https://github.com/vayun-networks/bracken-observability) should own collection and alerting conventions. Content caching and HTTP delivery belong in [bracken-cdn](https://github.com/vayun-networks/bracken-cdn).

## Planned milestones

1. Select initial resolver and authoritative service components.
2. Document configuration and zone management APIs.
3. Implement a local test environment with caching and health reporting.
4. Add DNSSEC workflows with key handling and rollover documentation.
5. Evaluate health-aware responses and traffic steering with explicit failure semantics.

## Operational and security considerations

DNS services are exposed to malformed input, abuse, and amplification risks. Deployments should define recursion access controls, rate limits, logging and privacy expectations, key protection, and recovery procedures. Do not expose a recursive resolver publicly unless its access policy and abuse controls are explicitly configured and tested.

## Development

No implementation or run commands are currently defined. Future instructions should include local test setup, sample zones, validation commands, and safe test boundaries.

## Related components

- [bracken-control-plane](https://github.com/vayun-networks/bracken-control-plane)
- [bracken-cdn](https://github.com/vayun-networks/bracken-cdn)
- [bracken-analytics](https://github.com/vayun-networks/bracken-analytics)
- [bracken-observability](https://github.com/vayun-networks/bracken-observability)