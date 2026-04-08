### Diagrama de Classes - Sistema de Eventos
```mermaid
classDiagram
    class Usuario {
        <<Abstract>>
        +String nome
        +String cpf
        +String email
    }

    class Aluno {
        +String matricula
    }

    class Professor {
        +String departamento
    }

    class Organizador {
        +registrarPresenca(Inscricao inscricao)
    }

    class Evento {
        +String titulo
        +DateTime data
        +int cargaHoraria
        +int limiteVagas
    }

    class Inscricao {
        +DateTime dataInscricao
        +StatusInscricao status
        +boolean presencaConfirmada
        +gerarCertificado()
    }

    class Palestrante {
        +String nome
        +String miniCurriculo
    }

    class StatusInscricao {
        <<Enumeration>>
        PENDENTE
        CONFIRMADA
    }

    %% Relacionamentos
    Usuario <|-- Aluno
    Usuario <|-- Professor
    Usuario <|-- Organizador

    Usuario "1" -- "0..*" Inscricao
    Evento "1" -- "0..*" Inscricao
    Evento "1" -- "1..*" Palestrante
    Inscricao .. StatusInscricao
