# Installation

C'est un package python à installer globalement (en dehors des venv. Au pire, il suffit de l'installer manuellement sur
chaque projet si l'installer globalement ne marche pas).

```shell
pip install pre-commit
```

Ensuite, il faut récupérer les fichiers de configuration depuis ce repo Github (cela changera peut-être en fonction de
l'intégration dans nos outils interne). Ces fichiers doivent être placés dans le dossier code.

Dans le dossier code, lancer la commande `pre-commit install` qui ajoutera un hook dans `.git/hooks/pre-commit`.
Cela permettra que pre-commit se lance avant chaque commit. Les commits seront impossible tant que pre-commit ne passera
pas. Il est possible d'éviter ce check avec `git commit -m "..." --no-verify` (pour Pycharm, décocher la case _"Run Git
Hooks"_ dans les 3 points dans la zone de texte d'écriture des commits). Pre-commit va vérifier uniquement les fichiers
modifiés, et va essayer de fix si possible.

Il est possible de lancer manuellement avec `pre-commit run` et pour tous les fichiers avec `pre-commit run --all-files`.

# Explications des fichiers

- `editorconfig` : Pour VSCode, installer l'extension editorconfig. Ce fichier permet de changer les paramètres d'édition pour les éditeurs de code. On peut mettre des règles spécifiques, par extension de fichier. Cela permet d'unifier les styles d'écritures de tout le monde.
- `eslintrc.yml` : fichier utilisé pour le style/règles Javascript à utiliser. Permet de définir la version JS utilisé, les règles avec leur sévérité, et autres options.
- `pre-commit-config.yaml` : C'est le fichier de base qui détermine quels fichiers sont inclus/exclus de la vérification pré-commit. C'est également ici que tous les outils de vérifications sont appelé, avec leurs ordre de passage et les arguments passés.
- `prettierrc.yml` : ce fichier est utilisé pour le style des fichiers autres que JS/Python. Il va formater les fichiers xml
- `pylintrc` : Ce fichier contient l'ensemble des règles pythons qui seront vérifiées, ainsi que les règles du plugin odoolint. Ces règles peuvent être supprimées au besoin.
- `pylintrc-mandatory` : ce fichier est similaire à .pylintrc mais là, il contient les règles qui doivent obligatoirement passer.
- `.ruff.toml` : ce fichier est celui qui gère toutes les règles de formatage/erreur/avertissement pour chaque linter Python et plugin. On peut y mettre les règles à ignorer, à ajouter, la version python ciblé, ainsi que les différents plugin tel que isort qui tri les imports, ou mccabe qui permet de vérifier la complexité du code selon la mesure de McCabe.
