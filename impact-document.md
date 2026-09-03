# Impact Document — Bharath Kumar Thulasidoss

> Master repository of all projects, initiatives, and measurable outcomes across Uber and Zomato.
> Use this as the single source for tailoring resumes, outreach messages, and interview stories.

---

## Uber | Software Engineer II — Data Platform (Aug 2024 – Present)

> **Team:** Databook (Data Platform org) | **Role:** SME for uMetadata service & vis-databook-graphql frontend
> One of the first engineers during the team's transition from US to India. Ramped up quickly to become an owner of mission-critical services spanning backend (Go, data pipelines), frontend (React, GraphQL), and data infrastructure (Hive, Spark, Kafka, Flink, Piper).

---

### Schema Evolution for Hive Tables (Batch Schema Service)
| Dimension | Detail |
|-----------|--------|
| **What I did** | Led the design and implementation of a brand-new Batch Schema Service (BSS) from scratch — Uber's dedicated schema management system for Hive/Hudi tables. Decoupled batch and real-time schema management, added rules-based validation, review/acknowledgement workflows, and region-aware DDL application via Databook UI. |
| **Technical depth** | Provisioned databases, network traffic groups, clean architecture. Built STS+HMS integrations with connection pooling, load balancing, health checks, and periodic connection refresh. Created a reusable connection library reducing STS startup latency by 30s. Built TAS+HMS and TAS+STS integrations for first-of-its-kind region-aware routing. Implemented PKINT-based Kerberos auth (early adopter, replacing EOL Keytab). Solved JVM classpath conflict between STS and HMS clients via shading-based build config. Built unified git+phab library with transaction-level isolation. Designed tree-based schema editor UI with full lifecycle management and G4 funnel metrics. |
| **Impact** | Decoupled **5,500+ assets** from the fragile real-time schema service. Enabled safe schema evolution with reader/writer protection — first of its kind at Uber. Reduced on-call load on schema service team. |
| **Scale** | 5,500+ assets, multi-engine (Presto, Spark, Hudi), region-aware writes |
| **Leadership signal** | Led the entire project end-to-end: requirements gathering, system design, implementation, task breakdown, and coordination with 6+ teams (Kafka, Hudi, Ad Tech, OneETL, uAccess, uWorc) and L6-L8 engineers. Proactively owned UX design (created Figma wireframes, got alignment from external designer and PM). |
| **SD3 signal** | Single-threaded technical leadership of a multi-quarter platform initiative. Influenced across org and seniority boundaries. Solved hard platform constraints (JVM classpath, Kerberos auth) without rewrites. |

### Data Co-Pilot (Multi-Agent AI)
| Dimension | Detail |
|-----------|--------|
| **What I did** | Designed and built a multi-agent orchestration framework using LangGraph and Python for contextual search and discovery of data assets. |
| **Technical depth** | Multi-agent orchestrator with specialized agents for intent classification, context embeddings, Q&A, and review. Exposed API server as MCP server for tooling integration. |
| **Impact** | Adopted by **10,000+ users** for data discovery. Improved discovery efficiency by **85%** — reduced average time-to-find from ~25 minutes to under 3 minutes. |
| **Scale** | 10,000+ active users, multi-agent coordination |
| **Leadership signal** | Identified the problem independently, proposed the solution, built a prototype, gathered usage data to make the business case, and drove adoption across engineering teams |
| **SD3 signal** | Influence without authority — no mandate to build this, led through demonstration. Became an official platform tool. |

### Glossary on Databook
| Dimension | Detail |
|-----------|--------|
| **What I did** | Designed and built Uber's centralized business glossary feature from MVP to production — enabling standardized business terminology and data-asset categorization across the company. |
| **Technical depth** | Reused existing graph-based architecture for data modeling. Implemented access control, OpenSearch indexing for discovery, pluggable CustomFields (key-value schema extension), related terms linking, bulk upload (CSV→Thrift→RPC), term archival support. Created UX wireframes and user flows from scratch in Figma. |
| **Impact** | Onboarded **2 teams** to glossary. Onboarded an **AI agent** to use glossary as knowledge base for enhancing outputs. Customer teams performed bulk uploads with positive UX feedback. Standardized business terminology across Uber. |
| **Scale** | Company-wide business glossary, extensible domain model |
| **Leadership signal** | Played PM + designer + engineer role — created UX from scratch, worked with director-level stakeholders. Led all enhancements: ownership protection, bulk onboarding, term linking. |
| **SD3 signal** | Cross-functional execution (design, product, eng). Customer-driven requirements shaping. Designed for long-term extensibility without schema rigidity. |

### Cloud-Aware Hive Metadata
| Dimension | Detail |
|-----------|--------|
| **What I did** | Led implementation of cloud-region awareness in uMetadata to accurately track independent copies of Hive datasets across on-prem and cloud zones. Introduced AreaIdentifier and hive_copies_info for independent lifecycle management. |
| **Technical depth** | Modified read/write APIs for union logic across timestamps and area identifiers. Updated Thrift/JSON schemas and mappers. Comprehensive E2E and unit tests. Added upsert/delete metrics and enhanced logging. Used Flipr-based percentage rollout — first time this approach was used in the metadata ecosystem. |
| **Impact** | Enabled accurate tracking of **1M+ Hive datasets** across cloud and on-prem. Restored **~86,000 previously untracked copies**. Reduced batch pipeline runtime from **~8h to ~5h**. Eliminated **3+ weekly cross-team queries** about metadata inconsistencies (down to 0). |
| **Scale** | 1M+ datasets, multi-region (cloud + on-prem) |
| **Leadership signal** | Co-authored ERD, consulted with multiple stakeholders. Collaborated with senior engineers for task division and timely delivery. |
| **SD3 signal** | Long-term architectural judgment. Balanced velocity, safety, and correctness. Proactively eliminated a recurring class of on-call issues. |

### BigQuery Ingestion
| Dimension | Detail |
|-----------|--------|
| **What I did** | Added a new data-asset type in uMetadata to support BigQuery datasets, enabling the BI team to manage BigQuery metadata through Databook. Built end-to-end ingestion pipeline and extended backend APIs + UI. |
| **Technical depth** | Piper-based ingestion pipeline extracting metadata from BigQuery ecosystem, publishing to common Kafka topic. Extended uMetadata APIs and Databook UI for the new entity type with backward compatibility and observability. |
| **Impact** | Daily ingestion of **7K+ BigQuery tables** and metadata changes. Enabled **5+ non-technical analytics teams** to discover and manage BigQuery metadata via Databook. |
| **Scale** | 7K+ tables daily, continuous updates |
| **Leadership signal** | Technical owner coordinating between BigQuery, backend, and frontend teams. Steered design toward shared ingestion abstraction over BigQuery-specific path. Led engineers from BI and P&P teams. |
| **SD3 signal** | Roadmap influence — prioritized long-term platform consistency over short-term delivery. Translated non-technical business needs into concrete system design. |

### Metadata & Lineage Service (SME)
| Dimension | Detail |
|-----------|--------|
| **What I did** | Subject Matter Expert for Uber's metadata and lineage frontend and backend service. Responsible for ingesting metadata for all data assets (Hive, Pinot, MySQL, Cassandra) and surfacing them with data lineage. |
| **Technical depth** | Kafka + Flink streaming jobs for real-time ingestion, batch Airflow reconciliation jobs. Fixed HMS/uMetadata consistency issues (race condition in streaming job for virtual regions). Built reusable DSW script for resync. |
| **Impact** | Handles **1M+ RPM** for real-time ingestion. Reduced metadata ingestion latency from ~15 seconds to sub-second for streaming path. Maintained **99.95% uptime**. Reduced consistency bug/support tickets from **5-6 weekly to zero**. |
| **Scale** | All data assets at Uber, 1M+ RPM |
| **Leadership signal** | SME role — owns technical direction, troubleshooting, and cross-team coordination. Worked with cloud migrator team for consistency improvements. |

### UQL Support & Duplicate Columns Fix
| Dimension | Detail |
|-----------|--------|
| **What I did** | Identified and fixed a critical graph corruption issue in uMetadata caused by duplicate edges during recursive traversal. Traced root cause to duplicate rows in a 500M+ row column table caused by replication lag and missing unique index. Designed prevention + cleanup strategy. |
| **Technical depth** | Implemented real-time cleanup job removing **~100K duplicate graph edges**. Designed master DB reads in a high-throughput write path (~3K RPS) without downtime. Used Flipr-based percentage rollout at request level. Built Spark dump job for offline analysis. Onboarding uMetadata DB to UQL with primary indexes via Percona online tools. |
| **Impact** | Restored correctness of uMetadata graph traversal. Reduced **Slack complaints about data missing from 7+ per week to zero**. Prevented future duplicate creation in one of the highest-throughput write paths. |
| **Scale** | 500M+ row table, ~3K RPS write path |
| **Leadership signal** | End-to-end ownership from detection to mitigation to long-term prevention. Made deliberate trade-off to avoid adding unique index (stop-the-server MySQL operation) in favor of read-consistency-based prevention. |
| **SD3 signal** | Advanced distributed systems debugging. Judgment under extreme scale constraints. Go-to expert for graph integrity. |

### Concurrency Utilities & Batch Tags Optimization
| Dimension | Detail |
|-----------|--------|
| **What I did** | Designed and implemented reusable concurrency primitives for uMetadata Go services: worker pool with bounded goroutines, priority scheduling, fail-fast/full-completion semantics. Built SafeGo utility for panic recovery. Refactored tag injection for parallelism. |
| **Technical depth** | Worker pool supporting batch and single-task execution, bounded goroutine usage preventing OOM. SafeGo with panic recovery and monitoring. Refactored single heavy SQL query into parallel calls. |
| **Impact** | Achieved **20x p99 latency improvement** for a core API. Eliminated classes of goroutine leak and unhandled panic failures. |
| **Scale** | Platform-level primitives used across uMetadata services |
| **Leadership signal** | Socialized utilities with team, guided adoption, reviewed integrations for concurrency correctness. |
| **SD3 signal** | Building shared infrastructure primitives. Creating extensible system abstractions. Preventing future incidents through proactive enablement. |

### DLM Stashing Datasets Cleanup
| Dimension | Detail |
|-----------|--------|
| **What I did** | Traced discovery bloat in Databook to DLM stashing tables being ingested into search and agent pipelines without filtering. Implemented guardrails and executed large-scale cleanup. |
| **Technical depth** | Filtering logic preserving legitimate DLM use cases while removing noise. Incremental, safe, reversible cleanup. Targeted OpenSearch node deletion. |
| **Impact** | Removed **~1.3M irrelevant datasets** from discovery. Reduced OpenSearch storage by **~100GB**. Improved search relevance and system stability. |
| **Scale** | 1.3M datasets, ~100M OpenSearch nodes, ~100GB storage |
| **Leadership signal** | Took ownership of a platform health issue without explicit roadmap ownership. Coordinated across search ingestion, backend, and UI layers. |

### DR Notifications on Databook
| Dimension | Detail |
|-----------|--------|
| **What I did** | Automated the previously manual process of notifying engineers about batch data failover drills. Built integration with TxE service for real-time failover notifications supporting regional/zonal and complete/partial failovers. |
| **Technical depth** | New RPC service (clean separation from existing). Hook in TxE service for API callbacks. Request-hash-based caching to prevent duplicate notifications. Leveraged existing notification service for targeted delivery. |
| **Impact** | Reduced failover SOP complexity. Saved engineer/TPM bandwidth during DR drills. Standardized notification targeting. |
| **Scale** | All batch data failovers, all Hive datasets and Piper pipelines |
| **Leadership signal** | End-to-end ownership. Cross-team testing with DR team. Proactively added caching for duplicate prevention (not a requirement). |

### Platform Reliability & Performance
| Dimension | Detail |
|-----------|--------|
| **What I did** | Fixed lineage ingestion drop from Spark data source v2 migration. Optimized critical APIs. Tuned Go GC. Added crash alerting. Built custom logging library with distributed tracing. Added exponential backoff for clients. Added Pinot dataset support in upsertDataset API. |
| **Technical depth** | Prevented ~40 lineage events/min from being dropped. Reduced getWorkloadsForDatasets p99 from **~30 min to <30s** via indexing + parallelism. Adjusted GOGC to trigger at 60% memory. Panic handlers + crash alerts. Trace ID-enabled logging library used across metadata ecosystem. Exponential backoff for resilience under partial failures. |
| **Impact** | Restored trust in lineage data. Unblocked safe cloud migrations. Reduced operational toil and on-call overhead. Raised baseline reliability of the metadata platform. |
| **Scale** | All metadata services, lineage pipeline, client libraries |
| **Leadership signal** | Partnered with Spark, lineage, and cloud migration teams. Proactively escalated lineage data loss as platform-level issue. Enabled Pinot team's v2 architecture migration. |
| **SD3 signal** | Platform ownership mindset. Multiplier effect through shared infrastructure. Shifting from reactive fixes to preventative improvements. |

### Batch Data Code Yellow
| Dimension | Detail |
|-----------|--------|
| **What I did** | Participated in batch data code yellow initiatives. Analyzed 10+ pipeline failures, RCA'd root causes, categorized them, and raised tickets on partner teams for proactive fixes. Part of DQ war room identifying bottlenecks. |
| **Technical depth** | Root-caused issues including: inefficient queries causing memory limit issues, misconfigured retries/timeouts in QR Python client, pipeline parallelism issues triggered from UI API calls, complex cross-pipeline timeout chains via DQ API calls. Even contributed a fix to Piper itself. |
| **Impact** | Proactively fixed **10+ pipeline failures** across multiple teams. Contributed upstream fix to Piper. Identified critical issues in partner team codebases. |
| **Scale** | Cross-org, multiple teams and services |
| **Leadership signal** | Deep-dived into codebases outside own domain. Raised fixes on partner teams. One Uber mindset. |

### Databook Open Source Migration Research
| Dimension | Detail |
|-----------|--------|
| **What I did** | Led research and feasibility analysis for migrating Databook to open-source metadata platforms (DataHub). Set up DataHub locally, created deployments, documented feature comparison and migration methodology. |
| **Technical depth** | Proposed module federation architecture for frontend integration — first of its kind at Uber. Authored build-vs-adopt decision framework. Documented migration path for ownership, tiering, and other metadata systems. |
| **Impact** | Enabled the team to make an informed roadmap decision on build vs adopt. Influenced org-level technical direction. |
| **Leadership signal** | Complete project leadership: identified tasks from proposed architecture, broke into milestones, estimated effort for entire migration. |
| **SD3 signal** | Defines architectural direction. Evangelizes modern design patterns. Roadmap/prioritization influence at org level. |

### Data Notifications — uMetric & DSW Support
| Dimension | Detail |
|-----------|--------|
| **What I did** | Added backend and frontend support to enable uMetric and DSW assets in Databook's notification ecosystem. |
| **Impact** | Enabled creation of **500+ notifications** for these products. Increased adoption of Databook notification platform. |
| **Leadership signal** | Cross-codebase ownership (took frontend changes in uMetric and DSW repos). One Uber execution across product boundaries. |

### Pipeline Optimization & Cloud Migration
| Dimension | Detail |
|-----------|--------|
| **What I did** | Led end-to-end migration of 4 uMetadata pipelines to GCP cloud. Optimized long-running pipelines by redesigning execution patterns (per-entity → batch API calls) and tuning Spark resource allocation. |
| **Technical depth** | Migrated MapReduce to Spark. Introduced controlled Python concurrency. Separated compute-heavy vs I/O-heavy stages. Fixed latent hive_metastore_actions bug that had caused a production incident. |
| **Impact** | Reduced umetadata_to_hive_data_export runtime from **4+ hours to ~1 hour** (4x improvement). Unblocked organization-wide cloud-first goal. |
| **Scale** | 4+ pipelines, GCP migration |
| **Leadership signal** | Technical owner for uMetadata pipeline migration. Applied incremental architectural changes to reduce blast radius. |

### Test Coverage for Metadata Ecosystem
| Dimension | Detail |
|-----------|--------|
| **What I did** | Raised test coverage across metadata backend and frontend services. Designed a reusable Dependency Injection HOC testing utility for React, enabling deterministic testing of reducers, React Query API calls, and external dependencies. |
| **Technical depth** | Backend coverage raised to **80%+** across multiple uMetadata services. Unblocked component testing in lineage-ui (**13% → 60%**). Added 12 integration tests for vis-databook-graphql. DI-based testing utility became the recommended pattern across metadata frontend services. Defined coverage thresholds as quality gates. |
| **Impact** | Overall test coverage improved from **~60% to ~85%** across the metadata ecosystem. Reduced regression risk. Improved shipping confidence. |
| **Scale** | Multiple backend + frontend services |
| **Leadership signal** | Guided engineers on new testing patterns. Raised quality bar beyond local code changes. Worked with external team for integration testing. |
| **SD3 signal** | Setting engineering standards. Multiplier via reusable tooling. Standards-setting and evangelism. |

### Safe Deployment Initiative (2026 H1)
| Dimension | Detail |
|-----------|--------|
| **What I did** | Drove a comprehensive safe deployment initiative across the entire metadata platform ecosystem (uMetadata, ustruct-lineage, hive-listener, umetadata-faas). Built **100+ integration tests** across 3 tiers — NIT (deploy-time validation), CTF (continuous monitoring in production), and E2E (full lifecycle tests). Set up caller-level alerting, crawler metrics, and production safety guardrails. |
| **Technical depth** | **NIT (Deploy-time):** 38 tests covering all remaining uncovered uMetadata APIs (search, ownership, governance, tiering, ingestion, permissions, config change, data quality). Increased ustruct-lineage endpoint test coverage from **37.5% → 100%** (15 endpoints). Tests for write-path idempotency, large graph traversal (depth-10 within 30s), column-level lineage, invalid UUID error handling, search substring validation. **CTF (Continuous Monitoring):** CRITICAL-tier tests for getEntityInstanceByID (303 RPS). HIGH-tier tests for categorization (33.6 RPS) and updateEntity (17.4 RPS). 25 MEDIUM-tier tests across 9 APIs. Continuous flows for search SLA, governance SLA, batch SLA, governed status, tier excluded checks, multi-entity search, kafka NPE regression, pipeline enum regression, tier filter search. **E2E (Full Lifecycle):** Built shared test infrastructure (testutil package with client factories, exponential backoff, retry helpers). GCTF-01: Hive dataset lifecycle via HMS KCP — produces audit log events to Kafka Consumer Proxy and verifies side effects via uMetadata read APIs. GCTF-02: Lineage ingestion via KCP — heatpipe-encoded unified lineage messages via YARPC gRPC. CTF-GOV-01: Governance lifecycle (onboarding, category verification, ungoverning). CTF-TIER-01: Tiering workflow (default tier, CheckTierStatus, UpdateDataset). CTF-TAG-01: Tag propagation via lineage. **Flink pipeline tests (java-code):** 10 tests covering deduplication, aggregation, and filtering in HmsAuditLogTransformerJob — prevents regression of the 2025-12-29 incident (malformed JSON from non-active HMS replicas). **Hive listener NITs (java-code):** 10+ KCP handler tests with uMetadata verification. **Alerting & Monitoring:** Generated MonCon for caller-level alerting. Added crawler error metrics for upsert drops. MySQL total count metrics for day-over-day drop detection. **Safety fixes:** Fixed nil pointer dereference in injectSLADefaultsIfExists. Mapped invalid request errors from 5xx → 4xx (reducing false alarms). Fixed NIT tests from mutating production data (switched to ConsumerName-based auth). Fixed test flakiness from MySQL replication lag (reusable RetryWithBackoff helpers). Fixed DLM onboarding failure for TTL > 2 years. Fixed uOwnAsset JSON field collision in search deserialization. Switched pingless ustruct-lineage from TChannel to HTTP with increased timeout. |
| **Impact** | **100+ integration tests** added across the metadata platform. uMetadata API endpoint coverage: **0% → 100%** for deployment-time validation. ustruct-lineage endpoint coverage: **37.5% → 100%**. Continuous monitoring in production for all CRITICAL/HIGH/MEDIUM traffic APIs. Full lifecycle E2E validation across Hive ingestion, lineage, governance, tiering, and tags. Prevented regression of 2+ past incidents via targeted regression tests. Reduced false 5xx alerts by fixing error classification. |
| **Scale** | 3 Go services (uMetadata, ustruct-lineage, hive-listener), 1 Java service (umetadata-faas), 100+ tests, 3-tier test framework (NIT/CTF/E2E) |
| **Leadership signal** | Single-handedly drove the entire safe deployment program for the metadata platform. Built shared test infrastructure reused across all test tiers. Identified and fixed production safety issues (tests mutating prod data, flaky tests masking real failures). |
| **SD3 signal** | Org-level safety initiative. Systematic approach to deployment confidence — not just writing tests, but designing a tiered testing strategy (deploy-time → continuous → lifecycle). Platform-wide standards-setting. Incident-driven test design (each regression test traces to a specific past incident). |

### Incident Debugging & On-Call Leadership
| Dimension | Detail |
|-----------|--------|
| **What I did** | Key escalation point during 2 major incidents and a partial service degradation. Root-caused issues across batch pipelines, snapshot generation, and downstream consumers. |
| **Technical depth** | Traced partial population of snapshot Hive tables. Fixed cloud-specific hive_metastore_actions bug. Debugged degradation via profiling — traced to oversized log generation. Chose systemic fixes over local mitigations. |
| **Impact** | Timely resolution increased pipeline robustness, unblocked cloud migration, and unblocked service deployments. Set bar for incident documentation quality. |
| **Leadership signal** | Central role in incident bridges. Cross-functional coordination. Culture-setting for postmortem quality. |

### Misc Self-Driven Platform Improvements
| Dimension | Detail |
|-----------|--------|
| **What I did** | Consolidated multiple ownership APIs into single paginated API. Added uOwn/pager presence validation for T1/T2 uptiering. Built column-level suggestions in search via new suggestor. |
| **Impact** | Reduced ownership page p99 from **10s to <500ms** via pagination. Made high-tier dataset uptiering more robust with on-call presence checks. Enabled column-level search suggestions for future use cases. |
| **Leadership signal** | All identified and prioritized independently without roadmap ownership. Proactive platform health improvements. |

### Mentoring & Knowledge Sharing
| Dimension | Detail |
|-----------|--------|
| **What I did** | Mentored intern on Databook stats project (from architecture to production). Onboarded new team member. Introduced NotebookLM knowledge base for metadata platform. Conducted 7-8 hiring interviews. Led sessions on frontend architecture, debugging, clean architecture, event loop, React rendering. |
| **Impact** | Intern delivered production-ready features independently. NotebookLM knowledge base received commendation from new joiners. Multiple frontend sessions improved team's cross-stack debugging ability. |
| **Leadership signal** | Multiplies impact through others. Creates psychological safety and growth. Acts as technical escalation point for mentees. |
| **SD3 signal** | Develops engineers. Knowledge multiplier. Sets bar for onboarding quality. |

---

## Zomato | SDE-II, Full Stack Engineer (Jun 2023 – Aug 2024)

### WebSocket Service Re-architecture
| Dimension | Detail |
|-----------|--------|
| **What I did** | Re-architected the real-time relay service for merchant orders. Migrated from EC2 + Auto Scaling with legacy socket.io to AWS ECS with uWebSockets. Implemented dual delivery mechanism using FCM/APNS push notifications as fallback via a notification service, ensuring message delivery even when WebSocket connections drop. |
| **Technical depth** | Pub-sub event processing architecture, ECS container orchestration, WebSocket protocol optimization, dual delivery via FCM/APNS notification service for guaranteed message delivery |
| **Impact** | Scaled from **100K to 500K+ concurrent clients**. Achieved **60% cost savings** (peak containers: 200 → 15). Improved event propagation latency by **20%**. |
| **Scale** | 500K+ concurrent clients, 100K+ pub-sub events/minute |
| **Leadership signal** | Drove the architecture decision, owned the migration end-to-end |

### Merchant Outlet Service
| Dimension | Detail |
|-----------|--------|
| **What I did** | Led a 2-person team to implement event propagation architecture with Kafka for high availability and fault tolerance. |
| **Technical depth** | Kafka event-driven architecture, Redis + DynamoDB read path, sub-5ms latency optimization |
| **Impact** | Service handles **1.5M read RPM** at **sub-5ms latency**. Achieved **99.99% availability** with zero-downtime deployments. Processed **500K+ fault-tolerance events/day** through Kafka with automatic retry and dead-letter handling. |
| **Scale** | 1.5M read RPM |
| **Leadership signal** | Led the team; made architecture decisions on data store selection and event propagation design |

### Analytics Insighting Service
| Dimension | Detail |
|-----------|--------|
| **What I did** | Built merchant analytics using Redis and Pinot. Created Spark ETL and Kafka pipelines to ingest data from offline Hive tables and production traffic. Engineered a YAML-based Querier. |
| **Impact** | Reduced widget creation effort from **weeks to under 1 day**. |
| **Scale** | Merchant-facing analytics across all Zomato restaurants |
| **Leadership signal** | Designed the YAML querier abstraction that democratized analytics widget creation |

### JavaScript Monorepo
| Dimension | Detail |
|-----------|--------|
| **What I did** | Orchestrated the development of Zomato's company-wide JavaScript monorepo using Vite, changeset-based versioning, and automated releases. Built packages for logger, telemetry, and Kafka publisher. |
| **Impact** | Boosted overall team productivity by **30%**. |
| **Scale** | Company-wide adoption at Zomato |
| **Leadership signal** | Drove org-wide developer experience improvement; built foundational packages used by all frontend teams |

### DevOps & Monitoring Pipelines
| Dimension | Detail |
|-----------|--------|
| **What I did** | Designed application monitoring with New Relic, Prometheus, Grafana, and Slack APIs for high-priority alerting. |
| **Impact** | Reduced response time to critical incidents by **60%**. Enhanced system stability. |
| **Scale** | All Zomato merchant-facing services |
| **Leadership signal** | Established monitoring best practices; integrated alerting across multiple tools |

### Mentoring
| Dimension | Detail |
|-----------|--------|
| **What I did** | Mentored a group of 3 full-stack developers. Conducted learning sessions on distributed systems, web fundamentals, networking, and databases. |
| **Impact** | Mentees ramped up and became independent contributors. Conducted **12+ structured sessions** over 6 months covering distributed systems, networking, databases, and web fundamentals. |
| **Leadership signal** | Proactive mentorship; knowledge sharing beyond immediate team responsibilities |

---

## Zomato | SDE-I, Full Stack Engineer (Jun 2021 – Jun 2023)

### Merchant Offers & Ads Platform
| Dimension | Detail |
|-----------|--------|
| **What I did** | Built payout, outlet, offers, and ads management features for the merchant dashboard. Redesigned order acceptance UX for increased urgency. |
| **Impact** | Features generated **Rs 50M revenue/month**. Reduced order acceptance time to under **17 seconds**. |
| **Scale** | All Zomato merchants |
| **Leadership signal** | Direct revenue impact; product thinking in UX redesign |

### Offline Order Dashboard
| Dimension | Detail |
|-----------|--------|
| **What I did** | Integrated service workers, caching, and FCM push notifications into the order dashboard, enabling offline functionality. |
| **Impact** | Saved approximately **80% of orders** placed during downtime through FCM-based relay. |
| **Scale** | All merchant order dashboards |
| **Leadership signal** | Identified a critical gap in reliability; implemented a creative solution with direct business impact |

### Ztrends (Flagship Product)
| Dimension | Detail |
|-----------|--------|
| **What I did** | Developed Ztrends, a flagship product showcasing food supply and demand across India for restaurant location intelligence. |
| **Impact** | Used by **100,000+ restaurateurs** for choosing restaurant locations. Averaged **200K+ sessions/month** across India. |
| **Scale** | Pan-India, 100K+ users |
| **Leadership signal** | Built a customer-facing product from scratch that became a flagship Zomato tool |

### Merchant Dashboard Platform
| Dimension | Detail |
|-----------|--------|
| **What I did** | Incorporated Immer and Emotion for scalable development. Built AST-based markdown parser, server state management, and list virtualization. Designed server-driven UI architecture. |
| **Impact** | Reduced UI interaction time by **30%** through web worker parallelism. Enabled quick product iterations via server-driven architecture. |
| **Scale** | Core merchant dashboard platform |
| **Leadership signal** | Platform-level thinking; built reusable infrastructure that accelerated the entire product team |

---

## Achievements & Differentiators

| Achievement | Detail | Use when... |
|-------------|--------|-------------|
| **Patent** | Rotatory Braille device for blind individuals (Patent No. 201911002013) | International applications — signals innovation beyond engineering |
| **Dean's Gold Medal** | Academic excellence, IIITD 2017-18 | Academic rigor; CGPA 9.04/10 |
| **SIH 2020** | 1st place, AMR track sponsored by Amazon | Hackathon wins, competitive drive |
| **QCRI 2018** | Best Project Award — "Tweet Classification and Visualization for Disasters" | NLP/ML background, research exposure |
| **CodeChef 5-Star** | Competitive programming | Problem-solving, algorithmic thinking |
| **CTF Top 10** | Team d4rkc0de | Security awareness, systems thinking |

---

## Behavioral Story Bank (STAR+R)

> Prepare these for SD3 interviews. The Agoda near-miss was on a leadership question — always have these ready.

### Story 1: Influence Without Authority
- **S:** Uber's data discovery was fragmented; engineers spent significant time finding the right datasets
- **T:** No mandate to build a new tool; needed to convince leadership to invest in Data Co-Pilot
- **A:** Built a prototype using LangGraph multi-agent framework, demonstrated value with early adopters, gathered usage data to make the case
- **R:** Adopted by 10,000+ users; became an official platform tool
- **Reflection:** Leading through demonstration is more effective than waiting for permission

### Story 2: Navigating Ambiguity
- **S:** Cloud region expansion for data discovery service — no existing playbook for reconciling 1M+ datasets across cloud and on-prem
- **T:** Needed to estimate capacity, design reconciliation, introduce region-aware tracking, and handle increased write load without downtime
- **A:** Co-authored ERD, introduced AreaIdentifier and hive_copies_info, used Flipr-based percentage rollout (first time in metadata ecosystem), estimated vertical scaling needs
- **R:** Accurately tracked 1M+ datasets, restored ~86K untracked copies, reduced pipeline runtime from ~8h to ~5h, eliminated 3+ weekly cross-team queries
- **Reflection:** Breaking ambiguous problems into measurable sub-problems makes them tractable

### Story 3: Technical Decision Advocacy
- **S:** Zomato's WebSocket service was hitting scaling limits at 100K clients on EC2 + socket.io
- **T:** Needed to propose and justify a complete re-architecture
- **A:** Benchmarked alternatives, proposed ECS + uWebSockets migration, built proof of concept showing 60% cost reduction
- **R:** Scaled to 500K+ clients, 60% cost savings, 20% latency improvement
- **Reflection:** Data-driven proposals with POC evidence get approved faster than theoretical arguments

### Story 4: Mentoring / Team Leadership
- **S:** Intern joined the Databook team for summer internship on the stats feature; also 3 new developers at Zomato with limited distributed systems experience
- **T:** Get them productive quickly while maintaining code quality and delivering production-ready features
- **A:** Co-authored ERD, introduced Pinot (first use case in metadata ecosystem), conducted sessions on clean architecture, event loop, React rendering. At Zomato, created structured sessions on distributed systems, networking, databases
- **R:** Intern delivered production-ready stats feature independently with positive feedback. Zomato mentees became independent contributors handling production incidents
- **Reflection:** Investing in people's fundamentals pays off more than giving them answers

### Story 5: Handling a Production Incident Under Pressure
- **S:** Major incident involving partial population of uMetadata snapshot Hive tables, affecting data correctness across Databook
- **T:** Root-cause the issue, restore service, prevent recurrence while downstream consumers were affected
- **A:** Traced failures across batch pipelines, snapshot generation, and downstream consumers. Authored detailed incident timeline. Chose systemic fixes over local mitigations. Fed learnings into pipeline and service design
- **R:** Resolution increased pipeline robustness, made cloud migration possible, unblocked deployments. Set bar for incident documentation quality
- **Reflection:** Production incidents teach you more about system boundaries than any design doc — always build in observability and graceful degradation from day one

### Story 6: Single-Threaded Ownership of a Platform Initiative (Schema Evolution)
- **S:** Uber's existing schema service for Hive/Hudi was paused due to operational fragility, incomplete coverage, and poor UX — leaving critical batch datasets without safe schema evolution
- **T:** Design and build a brand-new Batch Schema Service from scratch, coordinating across 6+ teams and L6-L8 engineers
- **A:** Led end-to-end: requirements, system design, implementation, UX design (Figma), task breakdown. Solved hard platform constraints (JVM classpath conflict via shading, PKINT Kerberos auth). Built unified git+phab library. Created tree-based schema editor UI
- **R:** Decoupled 5,500+ assets from fragile real-time service. Enabled safe reader/writer protected schema evolution — first of its kind at Uber. Reduced on-call load
- **Reflection:** The hardest part of platform work isn't the code — it's aligning stakeholders across seniority levels and making trade-offs that everyone can live with

### Story 7: Debugging at Scale (Duplicate Columns & Graph Corruption)
- **S:** uMetadata's recursive graph traversal was producing incorrect results due to duplicate edges. Source: a 500M+ row table with duplicate rows from replication lag
- **T:** Fix the corruption, prevent recurrence, and do it without downtime on a ~3K RPS write path
- **A:** Implemented real-time cleanup removing ~100K duplicate edges. Designed master DB reads for prevention (avoided adding unique index — a stop-the-server MySQL operation). Used Flipr-based rollout. Built Spark dump for offline analysis
- **R:** Graph traversal restored. Slack complaints dropped from 7+/week to zero. Prevented future duplicates in highest-throughput write path
- **Reflection:** At scale, the obvious fix (add a unique index) can be the most dangerous one. Understanding operational constraints is as important as understanding the code

---

## How to Use This Document

1. **Resume tailoring:** For each application, pick the 3-4 most relevant projects and rewrite bullets using: "Achieved [outcome] by [specific action] using [technology]"
2. **Outreach messages:** Pick ONE project with a metric that matches the target company's problem domain
3. **Interview prep:** Use the STAR stories above; prepare Stories 1, 2, and 6 especially for SD3 rounds (influence, ambiguity, single-threaded ownership)
4. **SD3 differentiation:** Highlight projects where you led across org boundaries (Schema Evolution, BigQuery Ingestion, Data Co-Pilot, Code Yellow)

### Quick Reference: Top SD3 Signals

| Signal | Projects to cite |
|--------|-----------------|
| **Single-threaded ownership** | Schema Evolution (BSS), Data Co-Pilot, Glossary, Safe Deployment Initiative |
| **Cross-org influence** | Schema Evolution (6+ teams, L6-L8), Code Yellow (10+ RCAs across orgs), BigQuery (BI+P&P teams), Safe Deployment (4 services, 100+ tests) |
| **Architectural judgment** | Cloud-Aware Metadata (Flipr rollout), UQL fix (avoided unique index), Open Source Migration (module federation) |
| **Platform multiplier** | Concurrency utilities (20x p99), Test coverage DI framework (60→85%), Custom logging library, Exponential backoff, Safe Deployment test infrastructure (reusable across all services) |
| **Customer impact** | Data Co-Pilot (10K+ users, 85% efficiency), Glossary (2 teams + AI agent), Ztrends (100K+ users) |
| **Incident leadership** | On-call leadership (2 major incidents), Code Yellow (10+ pipeline RCAs), Duplicate columns fix (7+/week→0 complaints) |

---

*Last updated: May 2026*
