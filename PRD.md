# PRD: Le Bangard Inc.

## Cahier des charges initial

Table des matières

Analyse du PRD Original
Contexte et Vision
Périmètre Fonctionnel Détaillé
Exigences de Conformité Alimentaire
Spécifications Techniques
Architecture et Intégrations
Expérience Utilisateur
Exigences Non-Fonctionnelles
Plan de Livraison Révisé
Analyse Financière et ROI
Gestion des Risques
Questions Résiduelles Priorisées


1. Analyse du PRD Original
1.1 Forces Identifiées
Le PRD original présente plusieurs points forts:
AspectÉvaluationCommentaireVision business✅ SolideObjectifs clairs de centralisation et d'efficacité opérationnelleApproche modulaire✅ ExcellenteLivraison incrémentale réduisant les risquesPropriété des données✅ StratégiqueCode et BD dédiés au client — avantage concurrentiel majeurIntégration IA✅ InnovantClassification automatique des courrielsModèle économique✅ TransparentPrix par module et hébergement fixe
1.2 Lacunes Critiques Identifiées
L'analyse révèle des lacunes significatives par rapport aux standards de l'industrie:
🔴 Lacunes Critiques (Impact Élevé)
1. Absence totale de conformité HACCP et traçabilité alimentaire

Le PRD ne mentionne pas les exigences du Safe Food for Canadians Regulations (SFCR)
Aucune traçabilité lot/batch des ingrédients
Pas de gestion des allergènes
Risque légal et opérationnel majeur pour un labo alimentaire

2. Gestion de production culinaire inexistante

Pas de planification des recettes
Aucun lien entre commandes et production
Pas de gestion des fiches techniques
Absence de calcul de coût recette

3. Module inventaire sous-spécifié

Traitement superficiel ("suivi des stocks")
Pas de gestion FIFO/FEFO obligatoire en alimentaire
Pas de dates de péremption
Pas de traçabilité des lots

🟡 Lacunes Importantes (Impact Moyen)
4. Boutique B2B incomplète

"Boutique cachée" trop vague
Pas de fonctionnalités clés: commandes récurrentes, prix personnalisés par client, minimums de commande

5. Intégration QuickBooks limitée

Synchronisation bidirectionnelle mentionnée mais pas détaillée
Pas de gestion du coût des marchandises vendues (COGS)
Pas de rapprochement inventaire/comptabilité

6. Gestion événementielle absente

Un traiteur gère des événements, pas seulement des commandes
Pas de calendrier événements
Pas d'affectation ressources/personnel

🟢 Lacunes Mineures (Impact Faible)
7. Horodateurs: fonctionnalités de base uniquement

Manque intégration avec planification de production
Pas de lien avec coût de main-d'œuvre par événement

8. Rapports et analytique non définis

"Tableaux de bord" mentionnés sans spécifications
Pas de KPI définis pour l'industrie

1.3 Benchmark Industrie
Selon les recherches, les logiciels de gestion traiteur leaders incluent systématiquement:
FonctionnalitéPrésent dans PRD originalStandard industrieGestion événements/calendrier❌ Non✅ OuiRecettes et costing❌ Non✅ OuiTraçabilité lots❌ Non✅ Oui (obligatoire SFCR)Gestion allergènes❌ Non✅ OuiPlanification production❌ Non✅ OuiFIFO/FEFO inventaire❌ Non✅ OuiPortail B2B self-service⚠️ Partiel✅ OuiIntégration comptable✅ Oui✅ OuiIA/Automatisation✅ Oui⚠️ Émergent

2. Contexte et Vision
2.1 Présentation du Client
Profil: Traiteur/laboratoire alimentaire québécois
Défis actuels:

Fragmentation des canaux de demandes (téléphone, courriel, site web)
Temps excessif consacré aux tâches administratives (estimé 15h/semaine selon standards industrie)
Absence de vue unifiée des opérations
Risques de non-conformité alimentaire sans traçabilité formelle

Contexte réglementaire: Assujetti aux réglementations de l'Agence canadienne d'inspection des aliments (ACIA) et potentiellement au SFCR si ventes interprovinciales ou exportation.
2.2 Vision Produit

Créer une plateforme opérationnelle complète qui centralise l'ensemble des activités d'un traiteur — de la demande client jusqu'à la livraison — tout en assurant la conformité alimentaire et l'efficacité opérationnelle.

2.3 Objectifs Stratégiques Révisés
#ObjectifIndicateur de succèsCible1Centraliser 100% des demandes% demandes dans le système100% en 6 mois2Réduire le temps administratifHeures/semaine tâches manuelles-50% (de 15h à 7.5h)3Atteindre conformité HACCPScore audit traçabilité100%4Améliorer marges produitsPrécision coût recette±2%5Augmenter ventes B2BCommandes via portail+30% en 12 mois6Réduire gaspillage alimentaire% pertes vs production-30%
2.4 Parties Prenantes
RôleResponsabilitésNiveau d'accèsPropriétaire/DirigeantDécisions stratégiques, rapports financiersAdministrateur completResponsable productionPlanification, recettes, contrôle qualitéModule production + inventaireResponsable commercialSoumissions, clients, événementsModule CRM + soumissionsEmployés cuisineExécution production, pointagePointeuse + instructions productionComptableFacturation, rapprochementsQuickBooks + rapportsClients B2BCommandes en lignePortail B2B externe

3. Périmètre Fonctionnel Détaillé
3.1 Module 1: Centralisation des Demandes et CRM
3.1.1 Objectif
Capturer et gérer toutes les interactions clients dans une vue unifiée, indépendamment du canal d'origine.
3.1.2 Fonctionnalités Détaillées
Capture multicanal:

Intégration courriel (Microsoft 365/Google Workspace via API)
Formulaires web (API REST vers site existant)
Capture téléphone (saisie manuelle avec horodatage)
Formulaires mobiles/tablettes (PWA)

Gestion des demandes:
ChampTypeObligatoireDescriptionSourceEnumOuiCourriel, Téléphone, Web, DirectType demandeEnumOuiSoumission, Commande, Support, InformationClientRelationNonLien vers fiche client (création si nouveau)PrioritéEnumOuiUrgente, Normale, BasseStatutEnumOuiNouvelle, En traitement, En attente client, FerméeAssigné àUtilisateurNonResponsable du suiviDate échéanceDateNonSLA selon typePièces jointesFichiersNonDocuments, images
Workflow automatisé:
Nouvelle demande → Classification IA →
  Si "Soumission" → Créer tâche soumission + Email accusé réception
  Si "Commande" → Vérifier client existant → Router vers production
  Si "Support" → Notifier responsable
SLA recommandés (basés sur pratiques industrie):

Soumission: réponse initiale < 4h ouvrables
Commande urgente: confirmation < 1h
Support: résolution < 24h

3.1.3 Assistant IA Courriels
Capacités:

Classification automatique

Analyse sémantique du contenu
Catégorisation: Soumission | Commande | Facture | Support | Spam/Promo
Confiance minimale: 85% pour action automatique, sinon révision humaine


Extraction d'informations

Date d'événement mentionnée
Nombre de convives
Type de service (buffet, cocktail, boîtes à lunch, etc.)
Budget mentionné
Restrictions alimentaires/allergènes


Actions automatiques paramétrables

Accusé de réception personnalisé
Création de tâche avec données pré-remplies
Association au client existant (matching par email/nom)
Alerte si client VIP ou commande importante



Règles de sécurité IA:

Jamais d'engagement de prix sans validation humaine
Jamais de confirmation de commande automatique
Journalisation complète des actions IA pour audit

3.1.4 Gestion des Clients (CRM)
Fiche client enrichie:
SectionDonnéesIdentificationNom, Adresse, Téléphone, Courriel, Type (B2B/B2C)FacturationAdresse facturation, Conditions paiement (Net 30, etc.), Limite créditPréférencesAllergènes à éviter, Préférences alimentaires, Notes spécialesHistoriqueCommandes passées, Montant total, Dernière commandeTarificationGrille de prix personnalisée (si B2B), Remises accordéesDocumentsContrats, Certificats (ex: organisme sans but lucratif)
Synchronisation QuickBooks:

Source de vérité: Plateforme pour données opérationnelles, QuickBooks pour données comptables
Champs synchronisés: Nom, Adresse, Conditions paiement, Balance à recevoir


3.2 Module 2: Gestion des Soumissions et Événements
3.2.1 Objectif
Transformer les demandes en soumissions professionnelles et gérer le cycle de vie complet des événements.
3.2.2 Fonctionnalités — Soumissions
Création de soumission:
ÉtapeActionsAutomatisation1. Informations de baseDate, lieu, # convives, type événementPré-rempli depuis demande2. Sélection menuChoix items du catalogue, personnalisationCalcul auto quantités3. Services additionnelsPersonnel, équipement, livraisonTarifs configurables4. Calcul prixCoût matières + marge + fraisAutomatique selon recettes5. Génération documentPDF professionnel brandéTemplate personnalisable6. EnvoiEmail avec suivi ouvertureRelance automatique J+3
Gestion des versions:

Historique complet des modifications
Comparaison entre versions
Validation requise pour changements post-acceptation

Statuts soumission:
Brouillon → Envoyée → Vue par client →
  → Acceptée → Convertie en commande
  → Refusée (motif à capturer)
  → Expirée (30 jours défaut)
3.2.3 Fonctionnalités — Gestion Événements (Ajout critique)
Vue calendrier:

Affichage jour/semaine/mois
Code couleur par type d'événement
Vue capacité production (charge cuisine)
Conflits de ressources visibles

Fiche événement:
SectionContenuGénéralClient, Date/heure, Lieu, # convives, Contact sur placeMenuItems confirmés, Quantités, Allergènes à gérerLogistiqueHeure début préparation, Départ livraison, InstallationPersonnelAffectations cuisine, Service, LivraisonÉquipementMatériel requis (chafing dishes, etc.)FinancierSoumission liée, Acompte reçu, SoldeDocumentsBL, Facture, Photos
Checklist pré-événement automatisée:

 Menu finalisé (J-7)
 Ingrédients commandés (J-5)
 Personnel confirmé (J-3)
 Équipement vérifié (J-1)
 Production lancée (selon recettes)


3.3 Module 3: Gestion de Production et Recettes (Nouveau module critique)
3.3.1 Objectif
Planifier et exécuter la production culinaire de manière efficace, traçable et rentable.
3.3.2 Gestion des Recettes
Fiche recette complète:
SectionDonnéesUtilisationIdentificationNom, Code, Catégorie, PhotoCatalogueIngrédientsListe avec quantités, unités, % perteCalcul coût, commandesAllergènesDéclaration obligatoire (14 allergènes majeurs)Conformité, étiquetageValeurs nutritivesCalories, macros (optionnel)Menu clientInstructionsÉtapes de préparationProductionRendementPortions, Poids finalPlanificationCoûtMatières premières, Main-d'œuvre, OverheadPrix de venteMédiasPhotos, Vidéos instructionsFormation
Calcul de coût automatique:
Coût recette = Σ(Ingrédient × Prix unitaire × (1 + % perte))
Coût portion = Coût recette / Nombre portions
Prix suggéré = Coût portion / Ratio food cost cible (ex: 30%)
Scalabilité des recettes:

Calcul automatique pour X portions
Alertes si quantités dépassent capacité équipement
Ajustements temps de cuisson suggérés

3.3.3 Planification de Production
Génération automatique:

Agrégation des commandes par date de production
Éclatement en recettes nécessaires
Calcul des besoins en ingrédients
Génération liste de préparation (prep list)
Ordonnancement selon contraintes (équipement, personnel)

Vue production quotidienne:
HeurePosteRecetteQuantitéStatut06:00PâtisserieMuffins fruits200⏳ En cours07:00ChaudSauce bolognaise15L⬜ À faire08:00FroidSalade César50 portions⬜ À faire
Intégration inventaire:

Vérification disponibilité ingrédients avant lancement
Réservation automatique des stocks
Alerte si rupture prévue

3.3.4 Contrôle Qualité Production
Points de contrôle HACCP intégrés:

Température réception marchandises
Température stockage (frigo/congélo)
Température cuisson (CCP)
Température maintien au chaud
Refroidissement rapide

Enregistrements obligatoires:
ContrôleFréquenceSeuil alerteActionTemp frigo2x/jour>4°CNotification immédiateTemp congélo1x/jour>-18°CNotification immédiateTemp cuissonChaque batch<74°C (volaille)Blocage production

3.4 Module 4: Inventaire et Traçabilité (Refonte majeure)
3.4.1 Objectif
Gérer les stocks avec traçabilité complète des lots, conformité HACCP, et optimisation des coûts.
3.4.2 Gestion des Articles
Fiche article:
ChampDescriptionExempleCode SKUIdentifiant uniqueING-FARINE-001NomDésignationFarine tout usageCatégorieClassificationIngrédients secsUnité stockUnité de mesurekgUnité achatUnité fournisseursac 20kgFacteur conversionAchat → Stock20FournisseursListe avec prixMetro: 18$/sacAllergènesDéclarationsGlutenDurée conservationJours après ouverture180Seuil réapprovisionnementQuantité minimale40 kgEmplacementLocalisation physiqueRéserve sèche - Étagère 3
3.4.3 Traçabilité des Lots (Critique SFCR)
Réception marchandises:

Scan ou saisie # lot fournisseur
Date réception
Date de péremption (DLC/DDM)
Quantité reçue
Contrôle qualité (température, état)
Photo optionnelle

Gestion FEFO (First Expired, First Out):

Suggestion automatique du lot à utiliser
Alerte lots proches péremption (J-7, J-3, J-1)
Blocage automatique lots expirés
Rapport lots à risque

Traçabilité bidirectionnelle:
En amont (rappel produit):
  Produit fini → Recettes utilisées → Lots ingrédients → Fournisseurs

En aval (traçabilité client):
  Lot ingrédient → Productions → Événements/Commandes → Clients livrés
Conservation des enregistrements:

Durée: minimum 2 ans (exigence SFCR)
Format: électronique, exportable
Accessibilité: disponible sur demande ACIA

3.4.4 Mouvements de Stock
Type mouvementDéclencheurImpactEntrée achatRéception fournisseur+Quantité, Nouveau lotSortie productionLancement recette-Quantité, Lien productionSortie perteDéclaration manuelle-Quantité, Motif requisAjustementInventaire physique±Quantité, JustificationTransfertEntre emplacementsMise à jour localisation
3.4.5 Réapprovisionnement Intelligent
Calcul besoins:
Besoin = (Commandes confirmées × Recettes)
       + Stock sécurité
       - Stock actuel
       - Commandes fournisseurs en cours
Suggestion commandes:

Regroupement par fournisseur
Optimisation minimum commande
Prise en compte délais livraison
Alerte si rupture prévisible

Lecture IA des listes de prix fournisseurs:

Formats supportés: PDF, Excel, CSV
Extraction: Article, Prix, Unité, Conditions
Validation humaine obligatoire avant application
Historique des prix pour analyse tendances


3.5 Module 5: Portail B2B et E-Commerce (Refonte majeure)
3.5.1 Objectif
Offrir aux clients professionnels une expérience de commande autonome, personnalisée et efficace.
3.5.2 Architecture du Portail
Accès sécurisé:

Authentification par invitation uniquement
MFA optionnel pour clients sensibles
Session timeout configurable
Journalisation des accès

Personnalisation par client:
ÉlémentPersonnalisationCatalogueProduits visibles selon contratPrixGrille tarifaire dédiéeMinimumsQuantité ou montant par commandePaiementConditions (Net 30, carte, etc.)LivraisonJours/créneaux disponiblesContactsListe des utilisateurs autorisés
3.5.3 Fonctionnalités E-Commerce B2B
Catalogue produits:

Navigation par catégorie
Recherche avec filtres (allergènes, disponibilité)
Fiche produit: photo, description, ingrédients, allergènes, formats
Prix dynamique selon quantité/client

Panier et commande:

Ajout rapide (code produit + quantité)
Commande récurrente (répéter commande précédente en 1 clic)
Modèles de commande sauvegardés
Validation stock temps réel
Sélection créneau livraison

Historique et suivi:

Liste commandes avec statuts
Téléchargement factures PDF
Suivi livraison (si intégration transporteur)
Relevé de compte

Fonctionnalités self-service:

Modification coordonnées
Gestion utilisateurs (admin client)
Déclaration allergies/restrictions
Demande de nouveaux produits

3.5.4 Règles Métier B2B
Cut-off commandes:

Configurable par jour livraison
Exemple: commande avant 14h pour livraison lendemain
Alerte client si approche cut-off

Gestion des indisponibilités:

Produit épuisé: affiché avec date retour estimée
Substitution suggérée si configurée
Notification client si produit commandé devient indisponible


3.6 Module 6: Facturation et Intégration Comptable
3.6.1 Objectif
Automatiser le cycle de facturation et maintenir la synchronisation parfaite avec QuickBooks.
3.6.2 Cycle de Facturation
Déclencheurs de facturation:

Événement: après livraison/exécution
B2B: selon fréquence client (chaque commande, hebdo, mensuelle)
Acomptes: à la confirmation de commande

Création facture:

Génération depuis commande/événement
Vérification données client
Application taxes (TPS/TVQ)
Génération PDF brandé
Envoi par courriel
Synchronisation QuickBooks

3.6.3 Intégration QuickBooks
Données synchronisées:
EntitéDirectionFréquenceSource de véritéClientsBidirectionnelleTemps réelPlateforme (création), QB (soldes)ProduitsPlateforme → QBÀ la modificationPlateformeFacturesPlateforme → QBÀ la créationPlateformePaiementsQB → PlateformeTemps réelQuickBooksCatégoriesConfiguration initialeManuelleQuickBooks
Mapping comptable:

Revenus par catégorie (Traiteur événement, B2B, Boutique)
Coût des marchandises vendues (COGS) lié aux recettes
Taxes configurables par type de vente

Gestion des écarts:

Rapport de réconciliation quotidien
Alerte si désynchronisation détectée
Journal des modifications pour audit


3.7 Module 7: Horodateurs et Gestion du Temps
3.7.1 Objectif
Capturer les heures travaillées avec précision, simplicité et lien à la production.
3.7.2 Fonctionnalités Pointeuse
Interface tablette:

Mode kiosque (écran dédié à l'entrée)
Identification: PIN, badge NFC, ou reconnaissance faciale (optionnel)
Actions: Punch IN, Punch OUT, Pause début/fin
Confirmation visuelle + sonore

Options de configuration:
OptionDescriptionRecommandationGéolocalisationValidation positionActivé si personnel mobilePhoto au punchPreuve visuelleOptionnel, considérations vie privéePunch automatiqueArrivée WiFi/BluetoothDéconseillé (imprécis)ArrondiRègles d'arrondi (5, 15 min)Selon politique RH
3.7.3 Gestion des Feuilles de Temps
Workflow validation:
Employé punch → Feuille générée →
Contremaître révise → Corrections si nécessaire →
Validation finale → Export vers paie/QuickBooks Time
Corrections autorisées:

Ajout punch oublié (avec justification)
Modification horaire (avec justification)
Approbation heures supplémentaires
Historique complet des modifications

3.7.4 Intégration Production (Valeur ajoutée)
Affectation temps par activité:

Lien punch → Événement/Production
Calcul coût main-d'œuvre par événement
Analyse rentabilité incluant temps réel


3.8 Module 8: Analytique et Tableaux de Bord
3.8.1 Objectif
Fournir une visibilité en temps réel sur les opérations et la performance financière.
3.8.2 Tableaux de Bord par Rôle
Direction:

Chiffre d'affaires (jour/semaine/mois/année)
Marge brute et évolution
Pipeline soumissions (valeur, taux conversion)
Top 10 clients par revenus
Alertes: créances en retard, stocks critiques

Production:

Charge de production (capacité utilisée)
Événements du jour/semaine
Ingrédients à réapprovisionner
Alertes: lots proches péremption

Commercial:

Soumissions en cours et statuts
Taux de conversion
Nouveaux clients
Relances à effectuer

3.8.3 KPIs Industrie Traiteur
KPICalculCible industrieFood Cost %Coût matières / Revenus28-35%Labour Cost %Coût main-d'œuvre / Revenus25-35%Taux conversion soumissionsAcceptées / Total>30%Délai moyen réponseTemps première réponse<4hGaspillage alimentairePertes / Production<5%Exactitude inventaireThéorique vs Physique>98%
3.8.4 Rapports Standards

Rapport de ventes (période, client, catégorie)
Rapport de production (volume, coûts, pertes)
Rapport d'inventaire (valeur, rotation, obsolescence)
Rapport de traçabilité (lots, mouvements)
Rapport de conformité HACCP (contrôles, écarts)
Rapport de temps (heures, coûts par projet)


4. Exigences de Conformité Alimentaire
4.1 Cadre Réglementaire Applicable
Règlement sur la salubrité des aliments au Canada (RSAC/SFCR):

Traçabilité obligatoire si ventes interprovinciales
Conservation enregistrements 2 ans minimum
Capacité de rappel en 24h

MAPAQ (Québec):

Permis d'exploitation
Formation hygiène et salubrité
Inspections périodiques

4.2 Fonctionnalités HACCP Intégrées
Les 7 principes HACCP supportés:
PrincipeSupport plateforme1. Analyse des dangersDocumentation recettes avec risques2. Points critiques (CCP)Contrôles température intégrés3. Limites critiquesSeuils configurables avec alertes4. SurveillanceEnregistrements automatiques5. Actions correctivesWorkflow si écart détecté6. VérificationRapports d'audit7. DocumentationArchivage complet 2+ ans
4.3 Gestion des Allergènes
14 allergènes prioritaires (Santé Canada):

Arachides
Noix
Graines de sésame
Lait
Œufs
Poisson
Crustacés
Mollusques
Soja
Blé/Triticale
Sulfites
Moutarde
Gluten (sources)
Lupin (ajout récent)

Fonctionnalités:

Déclaration obligatoire sur chaque ingrédient
Héritage automatique ingrédient → recette → menu
Alerte si commande contient allergène déclaré par client
Étiquetage conforme sur documents

4.4 Traçabilité et Rappels
Procédure de rappel simulée:

Identification du lot problématique
Requête traçabilité aval (30 secondes max)
Liste des clients/événements affectés
Génération communication de rappel
Documentation pour autorités

Test périodique recommandé:

Fréquence: trimestrielle
Exercice: tracer un lot aléatoire en <30 minutes
Documentation du test


5. Spécifications Techniques
5.1 Architecture Recommandée
┌─────────────────────────────────────────────────────────────┐
│                      CLIENTS                                │
├─────────────┬─────────────┬─────────────┬─────────────────│
│ App Web     │ App Mobile  │ Tablette    │ Portail B2B     │
│ (Staff)     │ (PWA)       │ (Pointeuse) │ (Clients)       │
└──────┬──────┴──────┬──────┴──────┬──────┴────────┬────────┘
       │             │             │               │
       └─────────────┴──────┬──────┴───────────────┘
                            │
                    ┌───────▼───────┐
                    │   API Gateway │
                    │   (REST/JSON) │
                    └───────┬───────┘
                            │
       ┌────────────────────┼────────────────────┐
       │                    │                    │
┌──────▼──────┐     ┌───────▼───────┐    ┌──────▼──────┐
│   Backend   │     │   Services    │    │     IA      │
│   (Node.js  │     │   Workers     │    │   Service   │
│   ou Python)│     │   (async)     │    │  (LLM API)  │
└──────┬──────┘     └───────┬───────┘    └──────┬──────┘
       │                    │                    │
       └────────────────────┼────────────────────┘
                            │
                    ┌───────▼───────┐
                    │   PostgreSQL  │
                    │   (données)   │
                    └───────┬───────┘
                            │
              ┌─────────────┼─────────────┐
              │             │             │
      ┌───────▼───┐  ┌──────▼──────┐  ┌───▼────────┐
      │ QuickBooks│  │   Email     │  │  Stockage  │
      │   API     │  │   (IMAP/    │  │  fichiers  │
      │           │  │   Graph)    │  │  (S3)      │
      └───────────┘  └─────────────┘  └────────────┘
5.2 Stack Technologique Recommandé
ComposantTechnologieJustificationFrontendReact + TypeScriptÉcosystème mature, PWA nativeBackendNode.js (NestJS) ou Python (FastAPI)API-first, performancesBase de donnéesPostgreSQLRobuste, JSON support, audit trailsCacheRedisSessions, données temps réelFiles d'attenteRabbitMQ ou Redis StreamsTâches async (email, IA)Stockage fichiersS3-compatible (MinIO si auto-hébergé)Documents, imagesIA/LLMAPI Claude ou GPTClassification courrielsAuthentificationJWT + OAuth2Sécurité standard
5.3 Exigences Base de Données
Audit trail obligatoire:

Toutes les tables critiques avec colonnes: created_at, updated_at, created_by, updated_by
Table d'historique pour modifications sensibles (prix, lots, contrôles)
Soft delete pour traçabilité

Performance:

Index sur champs de recherche fréquents
Partitionnement par date pour tables volumineuses (logs, mouvements)
Archivage automatique données >3 ans

5.4 Sécurité
Authentification:

Mots de passe: bcrypt, minimum 12 caractères
MFA: TOTP recommandé pour admins
Sessions: JWT avec refresh tokens
Verrouillage: après 5 tentatives échouées

Autorisation:

RBAC (Role-Based Access Control)
Permissions granulaires par module
Journalisation des accès sensibles

Données:

Chiffrement au repos (AES-256)
Chiffrement en transit (TLS 1.3)
Sauvegardes chiffrées

Conformité:

Loi 25 (Québec): consentement, droit d'accès, destruction
Audit de sécurité quotidien (service Orbit mentionné)


6. Architecture et Intégrations
6.1 Intégration QuickBooks Online
Méthode: API REST officielle Intuit
Flux de données:
EntitéOpérationsDéclencheurCustomerCreate, Read, UpdateCréation/modif clientItemCreate, Read, UpdateCréation/modif produitInvoiceCreate, ReadCréation facturePaymentRead, WebhookRéception paiementVendorReadImport fournisseursBillCreate (optionnel)Facture fournisseur
Gestion des erreurs:

Retry automatique (3 tentatives, backoff exponentiel)
File d'attente pour opérations échouées
Notification admin si échec persistant
Réconciliation manuelle possible

6.2 Intégration Email
Protocoles supportés:

Microsoft 365: Microsoft Graph API (recommandé)
Google Workspace: Gmail API
Autres: IMAP avec OAuth2

Architecture:
Boîte email → Polling (5 min) ou Webhook →
Queue traitement → Classification IA →
Actions automatiques → Stockage plateforme
Sécurité:

Accès lecture seule sur dossier spécifique (inbox ou dossier dédié)
Jamais de stockage mot de passe
Tokens rafraîchis automatiquement

6.3 Intégration Site Web
Options selon CMS:
CMSMéthodeComplexitéWordPress/WooCommercePlugin + API RESTMoyenneShopifyAPI REST + WebhooksFaibleCustomAPI REST bidirectionnelleVariableStatiqueRebuild via webhookFaible
Données synchronisées:

Catalogue produits (nom, description, prix, dispo)
Commandes entrantes (webhook)
Stock disponible (temps réel ou batch)

6.4 Intégrations Futures
Prévues:

QuickBooks Time (si retenu vs module interne)
Gestion Traiteur (si API disponible)
Transporteurs (Purolator, UPS) pour suivi livraison
Stripe/Square pour paiements en ligne


7. Expérience Utilisateur
7.1 Principes de Design
Pour environnement cuisine:

Boutons larges (min 48px) pour doigts/gants
Contraste élevé (lisibilité lumière variable)
Mode sombre optionnel
Feedback tactile/sonore
Résistance aux éclaboussures (UI, pas hardware)

Pour administration:

Navigation claire par module
Raccourcis clavier pour actions fréquentes
Recherche globale
Aide contextuelle

7.2 Parcours Utilisateur Clés
Parcours 1: Traitement d'une demande de soumission
1. Notification nouvelle demande (email ou push)
2. Vue demande avec infos extraites par IA
3. Clic "Créer soumission"
4. Formulaire pré-rempli, ajout items menu
5. Calcul automatique, ajustements manuels
6. Prévisualisation PDF
7. Envoi au client
8. Suivi statut (vu, relance, accepté)
Parcours 2: Planification production journée
1. Vue calendrier jour
2. Liste événements/commandes
3. Génération auto prep list
4. Vérification stocks (alertes si manque)
5. Affectation tâches au personnel
6. Impression/affichage instructions
7. Validation production (lots utilisés)
Parcours 3: Commande client B2B
1. Connexion portail
2. Navigation catalogue ou commande rapide
3. Ajout panier avec quantités
4. Vérification allergènes (warning si déclarés)
5. Sélection créneau livraison
6. Confirmation et paiement/commande
7. Email confirmation
8. Suivi statut
7.3 Responsive et Mobile
Breakpoints:

Mobile: <768px (PWA, punch employés)
Tablette: 768-1024px (cuisine, inventaire)
Desktop: >1024px (administration complète)

Mode hors-ligne (PWA):

Consultation recettes
Pointeuse (sync au retour connexion)
Liste de préparation


8. Exigences Non-Fonctionnelles
8.1 Performance
MétriqueCibleCritiqueTemps de réponse API<200ms (p95)<500msTemps chargement page<2s<4sTraitement email IA<30s<60sSync QuickBooks<5s par entité<15sGénération PDF soumission<3s<10s
8.2 Disponibilité et Reprise
AspectCibleDisponibilité99.5% (hors maintenance planifiée)Fenêtre maintenanceDimanche 2h-6hRPO (perte données max)1 heureRTO (temps reprise max)4 heuresSauvegardesQuotidiennes, rétention 30 joursSauvegardes hors-siteHebdomadaires, rétention 1 an
8.3 Scalabilité
Croissance prévue:

Utilisateurs: 10 → 50 sur 3 ans
Transactions/jour: 100 → 500
Stockage: 10GB → 100GB

Architecture:

Stateless backend (horizontal scaling)
Database read replicas si nécessaire
CDN pour assets statiques

8.4 Accessibilité

WCAG 2.1 niveau AA minimum
Navigation clavier complète
Labels ARIA pour lecteurs d'écran
Contraste minimum 4.5:1


9. Plan de Livraison Révisé
9.1 Phases Recommandées
Phase 0: Fondations (4 semaines)

Infrastructure et environnements
Authentification et gestion utilisateurs
Intégration QuickBooks (base)
Framework UI et composants communs

Phase 1: Socle Opérationnel (8-10 semaines)

Module Demandes et CRM
Assistant IA courriels (classification + extraction)
Module Soumissions (création, envoi, suivi)
Synchronisation QuickBooks (clients, produits, factures)

Phase 2: Production et Conformité (8-10 semaines)

Module Recettes et costing
Module Inventaire avec traçabilité lots
Contrôles HACCP intégrés
Planification production basique

Phase 3: Efficacité Opérationnelle (6-8 semaines)

Gestion événements et calendrier
Horodateurs sur tablette
Tableaux de bord et rapports
Intégration site web (produits)

Phase 4: Croissance (6-8 semaines)

Portail B2B complet
Commandes en ligne
Automatisation avancée courriels
Optimisations performance

9.2 MVP Recommandé (Phase 1)
Inclus:

Centralisation demandes (email, web, manuel)
CRM clients basique
Classification IA des courriels
Création et envoi de soumissions
Synchronisation QuickBooks (clients + factures)

Exclus du MVP:

Recettes et production (Phase 2)
Inventaire avec lots (Phase 2)
Portail B2B (Phase 4)
Horodateurs (Phase 3)

9.3 Jalons et Livrables
JalonDate cible*LivrablesJ0Semaine 0Kickoff, validation périmètreJ1Semaine 2Maquette interactive validéeJ2Semaine 4Environnement + auth + QB baseJ3Semaine 8Phase 1 en testJ4Semaine 10Phase 1 en productionJ5Semaine 18Phase 2 en productionJ6Semaine 26Phase 3 en productionJ7Semaine 34Phase 4 en production
*Dates relatives au démarrage projet

10. Analyse Financière et ROI
10.1 Estimation Budgétaire Révisée
Développement (estimation par module):
ModuleComplexitéEstimationPhase 0 - Fondations-8 000 - 12 000 $Phase 1 - Demandes + Soumissions + QBHaute18 000 - 25 000 $Phase 2 - Recettes + Inventaire + HACCPTrès haute22 000 - 30 000 $Phase 3 - Événements + Horodateurs + RapportsMoyenne15 000 - 20 000 $Phase 4 - Portail B2B + E-commerceHaute18 000 - 25 000 $Total développement81 000 - 112 000 $
Récurrent:

Hébergement managé: 200 $/mois
API IA (courriels): ~50-100 $/mois selon volume
Support et maintenance: à négocier

10.2 Comparaison TCO 5 ans
Scénario A: Solution sur mesure (proposée)
Développement:         95 000 $ (médiane)
Hébergement 5 ans:     12 000 $ (200 × 60)
IA 5 ans:               4 500 $ (75 × 60)
Évolutions (estimé):   20 000 $
─────────────────────────────────
Total:                131 500 $
Scénario B: SaaS multiples
Gestion Traiteur:      12 300 $ (205 × 60)
CRM (HubSpot/Zoho):     6 000 $ (100 × 60)
Inventaire (MarketMan): 9 000 $ (150 × 60)
Portail B2B (custom):  15 000 $
Intégrations custom:   20 000 $
Formation/setup:        5 000 $
─────────────────────────────────
Total:                 67 300 $
Analyse:

SaaS moins cher à court terme
Sur mesure: propriété, personnalisation illimitée, pas de dépendance
ROI sur mesure si besoins spécifiques (HACCP, B2B, IA)

10.3 Retour sur Investissement
Gains quantifiables estimés:
GainCalculValeur annuelleTemps administratif7.5h/sem × 52 × 35$/h13 650 $Réduction gaspillage2% CA × 500 000$ CA10 000 $Meilleur costing1% marge améliorée5 000 $Commandes B2B self-service10h/sem × 52 × 25$/h13 000 $Total gains annuels41 650 $
Payback période: ~2.5 ans sur solution complète

11. Gestion des Risques
11.1 Risques Identifiés
#RisqueProbabilitéImpactMitigationR1Intégration QuickBooks complexeMoyenneÉlevéPOC early, expertise dédiéeR2Adoption utilisateurs difficileMoyenneÉlevéFormation, UX simplifiée, champions internesR3Données historiques migrationHauteMoyenImport progressif, validationR4API "Gestion Traiteur" ferméeHauteMoyenPrévoir saisie manuelle ou remplacementR5Scope creepHauteÉlevéPRD signé, change managementR6Dépendance fournisseur IAFaibleMoyenAbstraction, fallback manuelR7Conformité HACCP insuffisanteFaibleTrès élevéValidation avec MAPAQ/consultant
11.2 Dépendances Critiques

QuickBooks API: Accès développeur requis, limites d'appels
Email provider: Accès API ou IMAP
Site web: Capacité technique d'intégration
Fournisseurs: Format standardisé des listes de prix


12. Questions Résiduelles Priorisées
12.1 Priorité Haute (Bloquant Phase 1)
#QuestionImpactPour quiQ1Quel fournisseur email (M365/Google/autre)? Accès API disponible?Intégration IAClient ITQ2Accès admin QuickBooks Online pour test API?Sync comptableClient/ComptableQ3Volume mensuel de demandes/soumissions/factures?DimensionnementClientQ4Charte graphique et branding existants?UX/MaquetteClient Marketing
12.2 Priorité Moyenne (Bloquant Phase 2-3)
#QuestionImpactQ5Avez-vous des fiches recettes existantes (format)?Migration recettesQ6Méthode actuelle de traçabilité lots (si existante)?Module inventaireQ7Certifications alimentaires détenues (HACCP, SQF, etc.)?ConformitéQ8CMS/plateforme du site web actuel? API disponible?Intégration webQ9Nombre d'employés à pointer et localisations?Module horodateur
12.3 Priorité Basse (Phase 4+)
#QuestionImpactQ10Nombre de clients B2B et volume commandes récurrentes?Portail B2BQ11Conditions de paiement par type de client?E-commerceQ12Intégration transporteur souhaitée?Livraison

Annexes
A. Glossaire
TermeDéfinitionCCPPoint de contrôle critique (Critical Control Point)FEFOFirst Expired First Out - méthode gestion stockHACCPHazard Analysis Critical Control PointsSFCRSafe Food for Canadians RegulationsPWAProgressive Web AppSKUStock Keeping Unit - code articleTCOTotal Cost of Ownership
B. Références
Sources recherche industrie:

Top Catering Management Software 2025
ACIA - Traçabilité alimentaire
Kitchen Production Software
B2B Food E-commerce
QuickBooks Restaurant Integration

C. Signatures
RôleNomDateSignatureClient - DécideurClient - OpérationsFournisseur - Chef de projetFournisseur - Tech Lead

---

## Design Direction

- **Style:** Charte Le Bangard Inc.
- **Palette:** [#000000] accent, bg-gray-900 background
- **Fonts:** Quattrocento / Quattrocento

---

## Historique des modifications

_Aucune modification pour l'instant_

---
*Créé le 2026-02-04T02:55:09.346Z*
*Job ID: 842c1870-4a56-48b0-a835-db5bc3afccc3*
